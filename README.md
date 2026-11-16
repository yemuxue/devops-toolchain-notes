# DevOps 工具链学习笔记

> 从「需求」到「上线」的工具链全景：**Jira/禅道 → GitLab → Nexus/Harbor → Kubernetes**

本仓库整理了一套关于 **DevOps 工具链** 与 **需求工程** 的学习材料，覆盖工具定位、能力边界、集成方式与选型判断。

---

## 一、核心脉络

| 层次 | 工具 | 回答的问题 |
|---|---|---|
| ① 需求 / 项目 / 缺陷 | Jira、禅道 | 做什么？谁做？进度如何？ |
| ② 代码与流水线 | GitLab、GitHub | 代码放哪？怎么评审？怎么自动构建？ |
| ③ 制品仓库 | Nexus（包）、Harbor（镜像） | 构建产物存哪？怎么分发和管控？ |
| ④ 运行环境 | Kubernetes | 跑在哪？ |

**一条主线：**

```
需求进 Jira/禅道 → 代码进 GitLab → 包进 Nexus、镜像进 Harbor → 容器由 K8s 运行
                                                    ↑
                         SonarQube / Trivy / Vault / Terraform / Ansible（横切）
```

---

## 二、目录结构

```
.
├── README.md                    本文件
├── 学习_v2_full.md              《需求工程全流程实践指南》主文档（16 阶段）
├── 学习.md                      早期版本
├── 学习.docx                    Word 版
├── 工具链能力域表.md             需求链路 8 阶段 + 交付/运维能力域 + 集成方式
├── 学习-流程图.drawio            16 阶段流程图（draw.io 源文件，可编辑）
├── 学习-流程图.png               上述流程图的导出图
├── phase-tool-matrix.png        16 阶段 × 工具能力域矩阵
├── 使用文档.md                   DOORS 全链路使用文档（CSV → DXL → 导入 → 校验）
├── 核心功能操作手册.md            DOORS 核心功能实操手册
└── diagrams/
    ├── capability-matrix.png    需求链路 × 交付流水线 能力域全景
    ├── toolchain-tables.png     工具链能力域表（三张表）
    └── phase-tool-matrix.png    矩阵图（另一版本）
```

---

## 三、图表说明

- **capability-matrix.png**：横向对比 DOORS / Jira / GitLab / Jenkins / TestRail 等在各阶段的「主责 / 参与 / 不涉及」，底部是交付运维流水线。
- **phase-tool-matrix.png**：16 个流程步骤 × 13 类工具域，标出每格的主责工具。
- **toolchain-tables.png**：三张表——需求链路 8 阶段主责软件、交付与运维能力域、5 种集成方式（手工到 OSLC）。
- **学习-流程图.drawio**：可编辑源文件，含 16 阶段与产品职责边界。

---

## 四、三条铁律（摘自主文档）

| 铁律 | 含义 | 违反的后果 |
|---|---|---|
| 唯一主责 | 每个阶段有且只有一个工具/角色负责 | 责任真空，出问题互相甩锅 |
| 双向可追溯 | 任一需求能查到「从哪来、到哪去」 | 变更漏改，测试漏测 |
| 变更受控 | 改需求必须走流程、留痕迹 | 版本混乱，交付对不上 |

---

## 五、学习路径

1. **基础**：Git、GitLab、Harbor、Nexus、Jira/禅道 —— 知道「东西放哪、流程怎么走」
2. **运行底座**：Linux → Docker → Kubernetes
3. **流水线**：GitLab CI / Jenkins → Argo CD
4. **可观测**：Prometheus + Grafana + Loki
5. **基础设施**：Terraform + Ansible
6. **质量与安全**：SonarQube、Trivy、Vault

---

## 六、说明

- 本仓库为个人学习整理，图表与文档基于公开资料与个人实践。
- `.docx` / `.png` 为派生产物，`.md` / `.drawio` 为可编辑源文件。
- 如需修改图表，请编辑 `学习-流程图.drawio` 后重新导出。
