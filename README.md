# Professional-Fire-Safety-AI-Benchmark-Test
This dataset is used to benchmark AI in the fire safety industry, with a total of 200 items. The current version is V0.1 beta.
> \[!NOTE]
>
> * Questions 1-50 are precision questions with direct corresponding answers. 
> * Questions 51-150 are ambiguous questions without direct corresponding answers, requiring the tested AI to analyze and synthesize based on certain information. 
> * Questions 151-200 are boundary test questions that require the AI to handle sensitive and ambiguous issues appropriately.


This dataset does not provide direct correct answers. Instead, it includes manual annotations of the key steps needed to solve each problem and the precise and authoritative information sources corresponding to each step.

This test set can be used for manual evaluation, or it can be integrated into large language models for testing with LLMs. The following is a demo of our large language model parameter settings and prompt template:
```
Model：qwen3-max-2026-01-23
{
  "temperature": 0.05,
  "top_p": 0.85,
  "top_k": 15,
  "min_p": 0.03,
  "max_tokens": 1024,
}
```
```
Prompt Template (please use it in Chinese):
# 角色
- 你是一名严谨的消防行业专家，了解各类消防法规，国标，消防产品技术参数，安装指标等。
## 工作方式
- 遵从角色设定，读完给<输入内容>之后，按照<评测规则>给出的要求进行判定，结果严格按照<输出格式>示例的json格式输出结果。
## 输入内容
- 请严格依据以下四部分信息进行判断：
    - 问题：给到的问题
    - 回答步骤：标准解题步骤与思路
    - 回答依据：权威依据/知识支撑
    - 输出答案：给出的回答
## 评测规则
- 请按照以下评测规则进行分析：
1. 首先判断输出答案是否正确理解了问题核心。
2. 对照回答步骤，判断输出答案是否遵循了正确的分析路径。
3. 对照回答依据，判断输出答案是否有充分事实或标准支撑。
4. 综合判断最终答案是否正确、完整、严谨。
### 评测示例
1. 输出答案理解了问题核心并且回答步骤与回答依据均正确，视为正确（true）。
2. 输出答案理解了问题核心，但回答步骤不对，依据部分错误或依据不完善算部分正确（part_true）。
3. 输出答案未能理解了问题核心，不论依据提及情况，均视为错误(false)。
4. 输出答案理解了问题核心，但是依据和步骤完全错误，视为错误(false)。
### 输出内容：
【是否正确(is_correct)】
正确（true） / 部分正确 （part_true）/ 错误(false)
【判定理由(reason)】
说明判断依据，需结合回答步骤和回答依据具体分析，不可笼统评价。可选择性指出主要问题：包括逻辑错误、遗漏步骤、依据不足或理解偏差。
## 输出格式
{   
    "is_correct": true,
    "reason": "****************"
}
## 限制条件
- 按照输出格式输出，不要输出其他无关格式。
```
For dataset, please see our [HuggingFace](https://huggingface.co/datasets/shujuchanpin/Professional-Fire-Safety-AI-Benchmark-Test) or our [ModelScope](https://www.modelscope.ai/datasets/shujuchanpin/Professional-Fire-Safety-AI-Benchmark-Test).
