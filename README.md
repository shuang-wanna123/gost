
# GOST Manager

一个用于 Debian / Ubuntu 的 GOST v3 多隧道管理脚本。
支持落地隧道和中转隧道。
支持 systemd 开机自启、隧道管理、批量操作、完整卸载。
创建中转隧道后会自动生成可直接导入 v2rayN 的 `ss://` 链接。

## 一键安装

```bash
bash <(curl -sL https://raw.githubusercontent.com/shuang-wanna123/gost-manager/main/ggv3.sh)
```

安装完成后，脚本会自动写入快捷命令：

```bash
gg
```

## 功能说明

落地隧道用于部署 Shadowsocks 服务端。
中转隧道用于把本机端口转发到落地机端口。
中转创建成功后，会自动显示导入链接，方便一键导入 v2rayN。
密码、端口、加密方式都支持手动设置，直接回车则使用默认值。

## 默认参数

默认落地端口为 `8443`。
默认中转本地端口为 `51520`。
默认密码为 `Qwert1470`。
默认加密方式为 `chacha20-ietf-poly1305`。

## 运行环境

建议系统为 Debian 12、Debian 13、Ubuntu 20.04 及以上。
脚本需使用 `root` 用户运行。
系统需安装 `systemd`。
下载 GOST 需要 `curl` 或 `wget`。

## 使用方式

运行脚本后，进入主菜单。
可以按提示添加落地隧道，也可以添加中转隧道。
创建完成后，脚本会自动生成对应的 systemd 服务。
后续可直接使用 `gg` 进入管理界面。

## 文件位置

GOST 程序默认安装到：

```bash
/usr/local/bin/gost
```

隧道配置默认保存到：

```bash
/etc/gost/tunnels
```

快捷命令默认安装到：

```bash
/usr/local/bin/gg
```

## 卸载

进入脚本主菜单后，选择“完全卸载”即可。
卸载会删除 GOST、本地配置、systemd 服务和 `gg` 快捷命令。

## 说明

本脚本当前基于 GOST v3。
脚本保留了原有菜单式管理结构，重点做了落地与中转的日常运维封装。
如果中转端需要生成可导入的 `ss://` 链接，填写的加密方式和密码必须与落地端实际配置一致，否则链接虽然能导入，但无法正常连接。

## 项目地址

GitHub 仓库地址：

```bash
https://github.com/shuang-wanna123/gost-manager
```
