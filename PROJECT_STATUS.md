# xuanze-content-workbench 项目状态

## 当前版本

v0.1

## 项目定位

这是一个围绕《选择之间》内容生产的本地工作台与 Codex 工作流系统。

它不是单纯网页工具，而是由三部分组成：

1. 本地 HTML 工作台
用于离线输入、展示、复制、导出和保存草稿。

2. xuanze-between Codex Skill
用于理解两难命题，生成《选择之间》风格的结构化内容素材。

3. 命题调集与内容审稿流程
用于从原始议题种子生成候选命题，再筛选、生成、审稿、精修和归档。

## 已完成模块

### 1. 本地 HTML 工具

相关文件：

- index.html
- index-v1.0-stable.html

状态：

- v1.0 已稳定
- 可本地打开
- 不依赖联网
- 不依赖 Supabase
- 不依赖 Vercel
- 支持输入命题、生成模板内容、复制 Markdown、导出 .md、保存草稿

说明：

index-v1.0-stable.html 是稳定备份，原则上不要修改。
index.html 是当前工作版本，但目前也保持稳定。

### 2. xuanze-between Skill

相关目录：

- .agents/skills/xuanze-between/

核心文件：

- .agents/skills/xuanze-between/SKILL.md
- .agents/skills/xuanze-between/examples/regression-test-prompts.md

状态：

- 已创建
- 已提交 GitHub
- 已能被 Codex 正确读取
- 已通过 7 条回归命题测试
- 已加入更严格的自检规则

作用：

负责把哲学、道德、亲密关系、AI、死亡、成长、记忆等命题转化成《选择之间》结构化内容。

### 3. 命题调集系统

相关文件：

- topics/raw-seeds.txt
- topics/generated-topics.md
- topics/selected-topics.md
- scripts/topic-transformer.md

状态：

- 已创建
- 已提交 GitHub
- 已完成真实测试
- 已能从原始议题种子生成候选命题池

作用：

将用户粘贴的热榜、评论观点、社会现象、个人想法，转化成《选择之间》风格的两难命题。

### 4. 内容输出系统

相关目录：

- outputs/

已生成文件：

- outputs/growth-rules-freedom.md
- outputs/growth-rules-freedom-revised.md

状态：

- 已完成第一条完整内容链路测试
- 已生成初稿
- 已经过审稿
- 已生成 revised 精修稿
- 已提交 GitHub

已完成命题：

如果努力只是让你更适应规则，而不是更自由，你还要努力吗？

精修标题方向：

你是在成长，还是被驯化？

### 5. 内容审稿器

相关文件：

- scripts/content-reviewer.md

状态：

- 已创建
- 已用于审查 outputs/growth-rules-freedom.md
- 初稿评分 86 / 100
- 建议小修后发布
- 已推动生成 revised 精修稿

作用：

判断输出内容是否真的适合发布，而不是只看结构是否完整。

审稿维度包括：

- 命题锋利度
- 核心价值冲突
- A/B 两难张力
- 内容原创感
- 分镜画面感
- 旁白传播力
- 发布标题

## 当前完整内容生产流程

当前 v0.1 的标准流程是：

1. 在 topics/raw-seeds.txt 中放入原始议题种子
2. 使用 scripts/topic-transformer.md 规则生成 topics/generated-topics.md
3. 从 generated-topics.md 中筛选命题，写入 topics/selected-topics.md
4. 使用 .agents/skills/xuanze-between skill 生成完整内容
5. 输出到 outputs/*.md
6. 使用 scripts/content-reviewer.md 进行内容审稿
7. 根据审稿意见生成 revised 精修稿
8. 将稳定输出提交到 GitHub

## 当前稳定状态

当前 GitHub main 分支已经包含：

- 本地 HTML 工具 v1.0
- xuanze-between skill
- skill regression checks
- topic collection workflow
- content reviewer workflow
- first content output
- first revised content output

当前稳定文件：

- index.html
- index-v1.0-stable.html
- .agents/skills/xuanze-between/SKILL.md
- .agents/skills/xuanze-between/examples/regression-test-prompts.md
- topics/raw-seeds.txt
- topics/generated-topics.md
- topics/selected-topics.md
- scripts/topic-transformer.md
- scripts/content-reviewer.md
- outputs/growth-rules-freedom.md
- outputs/growth-rules-freedom-revised.md

## 重要约束

后续开发必须遵守：

1. 不要随意修改 index-v1.0-stable.html
2. 修改 index.html 前必须先说明原因
3. skill 修改后必须重新跑 regression-test-prompts.md
4. 生成 outputs 后必须经过 content-reviewer 审稿
5. 不要把本地 HTML、skill、命题池、审稿器混成一个东西
6. 每次提交前都要确认 git status
7. 不要提交无关文件
8. 不要把 API key、Supabase key、个人隐私写入仓库

## 下一阶段方向

优先级从高到低：

### P1：批量生成 outputs

目标：

从 selected-topics.md 中一次选择多条命题，分别生成多个 outputs/*.md 文件。

注意：

批量生成前必须保证每条命题主题识别准确，不能为了数量牺牲质量。

### P2：自动审稿流程

目标：

让 Codex 对 outputs/ 目录下所有 Markdown 文件按 content-reviewer 标准批量审稿，输出 review 报告。

可能新增目录：

- reviews/

示例文件：

- reviews/growth-rules-freedom-review.md

### P3：命题池扩展

目标：

扩展 raw-seeds.txt 的来源，包括：

- 手动粘贴热榜标题
- 评论区观点摘要
- 社会现象
- 个人哲学问题
- AI / 亲密关系 / 死亡 / 道德 / 成长 / 记忆类议题

暂不做复杂爬虫。

### P4：发布准备

目标：

为每篇 revised 内容整理：

- 小红书标题
- B站标题
- 短视频脚本
- 分镜提示词
- 封面标题
- 标签建议

### P5：是否接 API

目前不接 API。

原因：

- 成本未确定
- 当前阶段核心问题是内容质量，不是自动化程度
- 本地 + Codex 工作流已经足够验证方向

## 当前判断

项目 v0.1 已经跑通。

它已经不是单纯网页，而是一个小型内容生产系统：

命题调集
→ 命题筛选
→ Skill 生成
→ Markdown 输出
→ 内容审稿
→ 精修归档

下一阶段重点不是继续堆功能，而是提高内容质量和流程稳定性。
