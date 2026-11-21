毛球收容所 · 网页前端

这是 `pet-sanctuary` 的构建产物（`vite build` 的输出），由帽子云从本仓库构建并部署。

## 结构

- `index.html` — 入口。资源路径是绝对的 `/assets/...`，**必须部署在域名根目录**，放子目录会全部 404
- `assets/` — 打包后的 JS/CSS，文件名带 hash，可长期缓存
- `pets/` — 毛球照片（Wikimedia Commons，自由授权）与 `credits.json` 署名信息

## 后端

游戏规则全部在浏览器端运行，进度存在 `localStorage`。

账号、云存档、亲和榜走 **Appwrite Cloud**（新加坡节点），前端直接调用 REST，
没有自建服务端，也没有 `/api` 反向代理。

源码里的 `server/` 与 Cloudflare Worker 是早期方案，**当前线上不参与运行**。

## 更新方式

在 `pet-sanctuary` 源码目录执行 `npm run sync:publish`（构建 + 覆盖本目录），
提交并推送本仓库，再到帽子云控制台点一次「重新部署」。

不要手改本目录里的文件 —— 它们会被下一次构建覆盖。
