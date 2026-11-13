# HR 招聘简历筛选技能包（hr-recruitment-skill）

一个面向 Agent 环境（如 LobsterAI）的 HR 简历筛选与分析技能包，把「一个装满简历的文件夹」变成「结构化、打分、排序后的候选人报告」。

## 功能模块

| 模块ID | 功能名称 | 说明 |
|--------|---------|------|
| D | **需求解析** | JD 逐条解析 → 等效替代推理 → 用人部门上下文理解 → 综合岗位需求 |
| A | **简历解析** | 文本提取 → 水分检测 → 质量评分 → 误分类检测 |
| B | **偏好挖掘** | 解析面试官反馈 → 挖掘未写入 JD 的隐性偏好 → HR 确认 |
| C | **候选人筛选** | 合并条件 → 硬性过滤 → 软性评分 → 排名 + 台账 |

四个模块共享同一工作区与进度系统，支持并行处理与断点续跑。

## 目录结构

```
hr-recruitment-skill/
├── SKILL.md                  # 技能主入口：触发条件、执行流程、模块编排
├── references/               # 各模块详细规范与参考数据
│   ├── module-A.md ~ D.md    # 四大模块的执行规范
│   ├── file-formats.md       # 输入/输出文件格式定义
│   ├── progress-system.md    # 进度系统设计
│   ├── parallel-processing.md# 并行处理规范
│   ├── directory-structure.md# 工作区目录结构
│   ├── execution-guide.md    # 执行指南
│   ├── tool-scripts.md       # 脚本使用说明
│   └── university-ranking.md # 高校排名参考数据
└── scripts/                  # Python 工具脚本
    ├── init_workspace.py     # 初始化工作区
    ├── progress_manager.py   # 进度管理
    ├── parallel_split.py     # 任务并行拆分
    ├── query_ranking.py      # 高校排名查询
    ├── pdf_to_png.py         # PDF 转 PNG
    └── ...
```

## 使用方式

将 `SKILL.md` 交给支持技能加载的 Agent 环境（如 LobsterAI / WorkBuddy），或在对话中直接引用本仓库。用户提到简历筛选、简历解析、候选人筛选、JD 分析等需求时自动触发。

## 边界说明

- 不从外部平台抓取简历（由 HR 提供文件）
- 不自动淘汰候选人（最终决策归 HR）
- 图片型 PDF 依赖模型多模态能力，无视觉能力时跳过
- 源文件（resumes/、feedback/、context/）只读，不做修改

## License

MIT
