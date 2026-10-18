# DSH Plugin Market Index

官方 DeepSeek Harness「插件 → 发现」页可直接使用的插件市场索引（**索引格式 1**）。

## 链接

```
https://cdn.jsdelivr.net/gh/online0618/jsDelivr-@main/index.json
```

用法：DSH 桌面端 → **设置 → 插件 → 发现 → 添加索引源**，粘贴上面的链接。

## 内容

- 288 个插件，均为「有 npm 包名」的条目，按 GitHub star 降序取前 300 后过滤得到
- 每个条目带**精确版本**、`publishTimestamp`（Unix 秒）、`engines.dsh` 兼容范围（有声明才写）
- 23 个分类（中英双语文案）
- 已用官方校验器 `@deepseek-ai/dsh-plugin-market-index` 的 `parseMarketIndex` 验证通过

## 更新方式

在 `D:\dsh\plugins\dshmarket-index\` 下重新生成：

```powershell
$env:TOP = "300"
node D:\dsh\work\tmp_gen_index.mjs
node D:\dsh\work\tmp_validate_index.mjs   # 必须先 VALID 再提交
git add index.json; git commit -m "refresh"; git push
```

数据源：本机桌面端宿主缓存的 dshmarket 目录（`http://127.0.0.1:3782/dsh-market/registry`，5065 条，上游每日 CI 刷新），再逐个向 npm registry 取精确 latest 版本与发布时间。

## 免责

非官方索引。收录不代表安全审核或兼容性保证；插件安装后以用户权限作为本地代码运行。
