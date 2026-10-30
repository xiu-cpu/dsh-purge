# dsh-purge — DeepSeek Harness 安全带评估插件（Fork 镜像）

> **本仓库是 [YuJunZhiXue/dsh-purge](https://github.com/YuJunZhiXue/dsh-purge) 的 Fork，非本人原创。**
> 原项目版权归原作者所有，遵循 **Apache-2.0**（见 [LICENSE](LICENSE)）及原作者附加条款。
> 按原作者要求：**衍生与再分发必须注明出处 YuJunZhiXue/dsh-purge；原始版本禁止转售。**
> 原始完整说明保留于 [README-upstream.md](README-upstream.md)（中文版见 [README.zh-CN.md](README.zh-CN.md)），一切以原文为准。

## 这是什么

dsh-purge 是面向**本机已安装的官方 DeepSeek Harness** 的红队 / 安全带评估插件。它的作用是在你自己的 DSH 安装里把"模型拒绝"与"宿主策略拦截"两层分开呈现，便于受控评估默认策略是否过严，并判断哪层拦下了请求。主要构成：

- **DSH 清除码头**：会话标题旁的入口，含"清理"与"钻机"两页
- **清理**：分组补丁状态、应用 / 恢复 / 卸载、提示词编辑器、多规则集
- **启动时**：自检后自动重放补丁，npm 覆盖后无需手动编辑 node_modules
- **主机政策**：改写默认文案、权限策略与工具限制；官方功能不受影响

版本对应：DSH 0.2.1-rc.2（0.2.0 仍可用）；**rc.3 及更新的 RC 不被支持**。

## 能力范围（原作者设定，必须遵守）

- 仅针对本机官方 Harness 包与本地配置；**不是**公网扫描器，也不是针对第三方系统的攻击工具包
- 开源版仅支持本地实验室：任务只允许回环与 RFC1918 地址；解析到公共 IP 的主机一律屏蔽
- 禁止游戏作弊（自瞄、穿墙、内存修改、反作弊绕过）
- 本构建不附带技能库或知识库

## 安装

```powershell
# 上游仓库
dsh plugin --profile "$env:DSH_PROFILE" add github:YuJunZhiXue/dsh-purge
# 或本 Fork
dsh plugin --profile "$env:DSH_PROFILE" add github:xiu-cpu/dsh-purge
```

## 法律与合规（摘要，完整原文见 README-upstream.md）

- 非营利开源项目，仅用于学习研究；下载、部署、运行、修改、分发的全部责任由使用者承担
- 禁止未经授权的入侵、攻击公共或私人系统、勒索、凭证填充、传播恶意载荷
- 禁止生成或传播法律禁止的内容；必须遵守《中华人民共和国刑法》《网络安全法》《数据安全法》《个人信息保护法》及模型供应商服务条款
- 与 DeepSeek 无任何关联；违规使用时许可证自动且不可撤销地终止

## 许可证

Apache-2.0（见 [LICENSE](LICENSE)，另有 [LICENSE-COMMERCIAL.md](LICENSE-COMMERCIAL.md) 与 [NOTICE](NOTICE)）。
衍生与再分发必须注明出处并命名来源仓库：**YuJunZhiXue/dsh-purge**。
