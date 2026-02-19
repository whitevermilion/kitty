# Kitty 终端配置 - 项目上下文

## 项目概述

这是一个用于 Kitty 终端仿真器的个性化配置目录。Kitty 是一个快速、功能丰富且 GPU 加速的终端仿真器。此配置包含定制的主题设置、字体配置、背景图像以及与其他工具（如 tmux）的集成。

**主要特点：**
- 使用 Catppuccin-Frappe 主题作为默认配色方案
- 配置了 0xProto Nerd Font 和 LXGW WenKai（霞鹜文楷）字体，支持中文显示
- 集成 tmux 作为窗口分割解决方案（禁用了 Kitty 内置分割）
- 支持背景图片和透明度调节
- 额外的"黑客"主题（黑底绿字）

## 目录结构

```
/home/red/.config/kitty/
├── kitty.conf           # 主配置文件
├── kitty.conf.bak       # 配置备份
├── current-theme.conf   # Catppuccin-Frappe 主题配置
├── hacker.conf          # 黑客主题配置（黑底绿字）
├── NatsumeStarDream.jpg # 背景图片
└── AGENTS.md           # 此文件
```

## 核心配置说明

### kitty.conf（主配置文件）

**字体设置：**
- 主字体：`0xProtoNerdFont`
- 粗体：`LXGW WenKai Bold`
- 斜体：`LXGW WenKai Light`
- 字体大小：16.0

**主题配置：**
- 默认主题：通过 `include current-theme.conf` 加载 Catppuccin-Frappe 主题
- 备用主题：`hacker.conf`（当前被注释）

**视觉效果：**
- 背景不透明度：0.75（75% 透明）
- 背景模糊：10 像素
- 光标轨迹：3 个光标残影
- 支持背景图片（当前注释，可取消注释启用）

**集成配置：**
- Shell：`/usr/bin/fish`
- 终端类型：`xterm-256color`（SSH 兼容）
- Shell 集成：已启用
- **tmux 集成**：已禁用 Kitty 的内置窗格分割（`kitty_mod+enter`），完全依赖 tmux 进行窗口管理

### current-theme.conf（Catppuccin-Frappe 主题）

这是一个舒缓的 Pastel 配色方案，基于 Catppuccin 设计系统。

**配色特点：**
- 背景色：`#303446`（深蓝灰色）
- 前景色：`#C6D0F5`（浅蓝色）
- 标签栏：Powerline 样式，紫色激活标签
- 16 种终端颜色，提供丰富的语法高亮支持

### hacker.conf（黑客主题）

纯黑客风格的黑底绿字主题。

**配色特点：**
- 背景：纯黑 `#000000`
- 前景/主色：亮绿 `#00FF00`
- 光标：绿色块状
- 标签栏：Powerline 样式，绿色激活标签
- 用于复古终端体验

## 配置管理

### 切换主题

在 `kitty.conf` 中修改主题引用：

**使用 Catppuccin-Frappe 主题（当前）：**
```kitty
include current-theme.conf
# include hacker.conf
```

**使用黑客主题：**
```kitty
# include current-theme.conf
include hacker.conf
```

修改后需要重新加载 Kitty 配置：
```bash
# 在 Kitty 中按 Ctrl+Shift+F5
# 或运行以下命令重新启动 Kitty
```

### 启用/禁用背景图片

在 `kitty.conf` 中取消/添加注释：
```kitty
background_image ~/.config/kitty/NatsumeStarDream.jpg
```

### 调整透明度

修改 `kitty.conf` 中的：
```kitty
background_opacity 0.75  # 值范围：0.0（完全透明）到 1.0（完全不透明）
```

## 开发与自定义约定

### Git 历史

项目经历了以下主要变更（从最新到最旧）：
1. **精简配置**：简化配置文件
2. **tmux 集成**：禁用 Kitty 内置窗格分割，完全使用 tmux
3. **黑客主题**：添加黑底绿字主题配置
4. **变更**：配置优化
5. **首次提交**：初始配置

### 添加新主题

如需添加新主题：

1. 创建新的 `.conf` 文件（例如 `my-theme.conf`）
2. 定义颜色方案（参考 `hacker.conf` 或 `current-theme.conf` 的结构）
3. 在 `kitty.conf` 中添加 `include my-theme.conf`
4. 注释掉其他主题引用

### 字体配置

中文字体使用 LXGW WenKai（霞鹜文楷），确保正确安装这些字体：

```bash
# 检查字体是否已安装
fc-list | grep -i "LXGW"
fc-list | grep -i "0xProto"
```

## 快捷键说明

- **Ctrl+Shift+F5**：重新加载配置文件
- **kitty_mod+enter**：已禁用（映射到 `no_op`），使用 tmux 的快捷键代替

## 外部依赖

- **Kitty 终端**：主要应用
- **tmux**：用于窗口和窗格管理
- **fish shell**：默认 shell
- **字体**：0xProto Nerd Font、LXGW WenKai

## 注意事项

1. 配置文件使用 `#` 作为注释符号
2. 所有颜色值使用十六进制格式（`#RRGGBB`）
3. 背景图片路径应为绝对路径或相对于 `~` 的路径
4. 修改配置后建议重新加载或重启 Kitty 以应用更改
5. SSH 连接时使用 `xterm-256color` 终端类型以确保兼容性

## 相关资源

- Kitty 官方文档：https://sw.kovidgoyal.net/kitty/
- Catppuccin 主题：https://github.com/catppuccin/catppuccin
- Nerd Fonts：https://www.nerdfonts.com/
- LXGW WenKai 字体：https://github.com/lxgw/LxgwWenKai