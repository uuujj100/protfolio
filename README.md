# NIGHT7 LAB · 技术作品集

2026 级人工智能专业学生的个人技术作品集。纯静态，零依赖，浏览器直接打开即可运行。

在线地址：https://uuujj100.github.io/protfolio/

## 目录结构

```
portfolio/
├── index.html            作品集首页
├── demos/
│   ├── n7-player.html    视频播放模块演示（可运行）
│   └── geomock.html      定位服务演示（可运行）
├── docs/
│   └── notes.md          技术笔记：分片预读、进度记忆、坐标转换、漂移处理
├── LICENSE
└── README.md
```

## 在线演示

| 演示 | 说明 | 涉及技术 |
| --- | --- | --- |
| [N7 Player](demos/n7-player.html) | 本地/远程视频播放，倍速、进度记忆、断点续播、键盘快捷键、**WebVTT 字幕** | HTML5 Video API、`TimeRanges`、`localStorage`、VTT 解析 |
| [GeoMock](demos/geomock.html) | 浏览器定位、WGS84→GCJ02 坐标转换、轨迹绘制与平滑采样、**手动坐标对比** | Geolocation API、坐标纠偏、haversine、移动平均 |

两个演示都不依赖任何框架，单文件即可运行，源码就是页面本身。

## 技术要点

- **进度记忆的 key 用「文件名 + 字节大小」**，而不是 blob URL —— 后者每次生成都不同。
- **大文件首帧卡顿**：`preload="metadata"` 只取元数据先开播，再按 `buffered` 区间顺序补齐。
- **定位坐标必须转 GCJ02**：GPS 原始坐标与国内地图坐标系在国内相差 300～500 米。
- **定位漂移先看 `accuracy` 再平滑**：精度半径过大的点先丢弃，再走移动平均。

细节见 [docs/notes.md](docs/notes.md)。

## 本地运行

下载仓库后直接用浏览器打开 `index.html`，无需安装依赖。
定位演示需要 HTTPS 或 `localhost`，`file://` 下浏览器会拒绝授权。

## 许可

MIT License，见 [LICENSE](LICENSE)。
