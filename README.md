# 云家居演示视频 · 网页版

把 `云家居视频.mp4` 做成了一个可以直接用浏览器打开、拖动进度条播放的网页，代码放在 git 仓库里，可直接推到 GitHub Pages 得到公网链接。

## 在线地址（已部署）

- 播放页：<https://zuyi90693-maker.github.io/Smart_Hom.github.io/>
- 视频直链：<https://zuyi90693-maker.github.io/Smart_Hom.github.io/yun-jiaju.mp4>
- 仓库：<https://github.com/zuyi90693-maker/Smart_Hom.github.io>

托管方式：GitHub Pages（`main` 分支根目录，Deploy from a branch）。

## 文件说明

| 文件 | 用途 |
| --- | --- |
| `index.html` | 视频播放页（深色卡片样式，含下载按钮） |
| `yun-jiaju.mp4` | 视频本体（原文件 `云家居视频.mp4`，640×368 / H.264 / 1:46 / 6.3 MB） |
| `poster.jpg` | 封面帧（实机图） |
| `server.js` | 本地静态服务器，支持 Range，手机/局域网可直接访问 |

## 本地访问（同一 WiFi 内任何设备）

```powershell
cd "D:\deepseek_harnss\talk_work\yun-home-video-site"
node server.js 8088
```

- 本机：<http://127.0.0.1:8088/>
- 手机 / 平板（同一 WiFi）：<http://192.168.10.10:8088/>

局域网访问需要防火墙放行 8088 端口（只放行一次即可）：

```powershell
New-NetFirewallRule -DisplayName "yun-home-video 8088" -Direction Inbound -Protocol TCP -LocalPort 8088 -Action Allow -Profile Private
```

## 推到 GitHub 变成公网链接（GitHub Pages）

前提：有 GitHub 账号，并在 <https://github.com/settings/tokens> 建一个带 `repo` 权限的 Personal Access Token（classic）。

1. 在 GitHub 新建一个**公开**仓库，名字随意，例如 `yun-home-video`（不要勾选初始化 README）。
2. 在本目录执行：

```powershell
cd "D:\deepseek_harnss\talk_work\yun-home-video-site"
git remote add origin https://github.com/<你的用户名>/yun-home-video.git
git branch -M main
git push -u origin main
```

3. 打开仓库 Settings → Pages，Source 选 `Deploy from a branch`，Branch 选 `main` / `root`，保存。
4. 等 1~2 分钟，链接就是：

```
https://<你的用户名>.github.io/yun-home-video/
```

也可以直接分享文件直链：
`https://<你的用户名>.github.io/yun-home-video/yun-jiaju.mp4`

> 说明：单文件 6.3 MB，远低于 GitHub 100 MB 上限，因此不需要 Git LFS；Pages 单站点限制 1 GB 也远够用。

## 本仓库 git 记录

已初始化为本地仓库并完成首次提交，只差一个远程地址即可推送。
