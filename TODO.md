# TODO

实验计划在 [ROADMAP.md](ROADMAP.md)·探索方向，本文件只记落地与工具侧的事，不重复那份清单（2026-10-21 起）。

## LLM 统一 prompt

- [ ] 通用 prompt vs 专用 prompt 对比误报识别率和 bug 发现率。判据：同一批样本各跑一轮，误报数与真 bug 数分别记，给两轮的结果并列

## 工具

- [ ] `reflect` 命令行入口：`src/reflect/` 已有 711 行库实现（`forward_slice` / `build_call_graph` / `impact_analysis` / `code_search` / `type_info`），crate 目前只有 lib、无 bin。达成标志：一个可执行目标，能从命令行指定文件、行号与模式，打印定向分析结果
- [ ] 置信度变量名表扩展：表是硬编码在 `src/llm.rs::compute_confidence` 里的 12 个名字（parts / price / qty / trim / parse / total / sum / v / name / threshold / items / item），换个领域的代码就锚不住。达成标志：名单移出函数或可配置，且在同一批样本上锚定率不低于现状

## 已关闭

- ✅ 模式 D：正向证据链 vs 反向追溯链 → 排序影响 LLM 关注点，已验证
- ✅ 假阳性过滤 3 轮实验 → 启发式 + LLM 两级流水线，已落地生产
- ✅ 证据不足时 LLM 编造分析 → 已验证现象，未量化频率
