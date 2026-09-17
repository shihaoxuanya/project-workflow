# 项目团队工作流 · project-workflow

一个用于 Codex 的个人技能：根据项目想法设计岗位分工，经确认后在当前项目下创建持久岗位任务，明确开工后自动交接、验收与有限返工。

## 工作方式

描述想法 → 查看岗位与协作方案 → 确认组队 → 创建任务并待命 → 明确开工 → 执行与验收。

- 适用于软件、内容、研究等项目，按交付物选择岗位，不固定为开发和测试。
- 每个团队由项目经理统一调度，岗位任务归属于同一个 Codex 项目。
- 确认分工仅授权创建团队，不会自动执行项目。
- 支持进度查看、暂停、恢复、重复交接检查与中断续接。
- 默认初次执行后最多追加 3 轮返工，外部阻塞单独报告。

## 安装

将本仓库克隆到个人技能目录下的 `project-workflow` 文件夹。目标文件夹已存在时先检查已有内容，不直接覆盖。

Windows PowerShell：

```powershell
git clone https://github.com/shihaoxuanya/project-workflow.git "$env:USERPROFILE\.codex\skills\project-workflow"
```

macOS / Linux：

```sh
git clone https://github.com/shihaoxuanya/project-workflow.git ~/.codex/skills/project-workflow
```

如果自定义了 CODEX_HOME，请使用其下的 skills 目录。确认 Codex 的可用技能列表已显示 project-workflow 后调用；若当前会话尚未发现，可新建会话再检查。

## 使用示例

```text
使用 $project-workflow，我想做一个电商平台，请分析需要哪些岗位并给出协作方案。
```

确认方案后，团队创建并待命。在项目经理任务中发送：

```text
开始项目：按已确认的方案实现首版。
```

也可发送“查看进度”“暂停协作”“恢复协作”。

## 文件

- `SKILL.md`：技能入口与使用边界。
- `agents/openai.yaml`：中文名称、描述与调用示例。
- `references/orchestration.md`：初始化、交接、成果同步与恢复协议。
- `assets/role-prompts.md`：岗位初始化和交接消息模板。

## 运行要求与限制

需要可用的 Codex 项目管理及任务创建、消息、读取和等待工具。岗位是项目下的平级持久任务，协作关系由技能维护，不是应用原生父子任务。

Git 项目默认使用 worktree，并显式同步交付版本；非 Git 项目对冲突写入采用串行执行。技能不默认设置定时唤醒，不是常驻工作流服务，运行依赖应用、工具和额度可用。

## 验证

通过技能格式校验，以及软件、内容、研究场景的独立行为模拟；覆盖授权边界、部分创建失败、重复派单、跨 worktree 交接、返工限制与暂停恢复。
