# HomeLede （Kernel 5.x) 版本说明
[1]: https://img.shields.io/badge/license-GPLV2-brightgreen.svg
[2]: /LICENSE
[3]: https://img.shields.io/badge/PRs-welcome-brightgreen.svg
[4]: https://github.com/xiaoqingfengATGH/HomeLede/pulls
[5]: https://img.shields.io/badge/Issues-welcome-brightgreen.svg
[6]: https://github.com/xiaoqingfengATGH/HomeLede/issues/new
[7]: https://img.shields.io/badge/release-v2020.09.05-orange.svg?
[8]: https://github.com/xiaoqingfengATGH/HomeLede/releases
[10]: https://img.shields.io/badge/Contact-telegram-blue
[11]: https://t.me/t_homelede
[![license][1]][2]
[![PRs Welcome][3]][4]
[![Issue Welcome][5]][6]
[![Release Version][7]][8]
[![Contact Me][10]][11]

[固件使用说明](https://github.com/xiaoqingfengATGH/HomeLede/wiki)

+ 基于Lede OpenWrt，多款HomeLede原创软件及Lienol等作者软件包（Feed）
+ 结合家庭x86软路由场景需要定制
+ 按照家庭应用场景对固件及软件进行测试（x86），通过后发布

对家庭路由高频功能进行了测试（x86软路由），保证可用。

## 固件内置功能
+ 提供私有软件服务器，实现软件全自动安装，无需手动处理软件包依赖
+ 支持UPnP（为BT、EMULE，家用摄像头、XBOX、PS4提供支持）
+ 支持CIFS文件共享协议（路由直接挂载NAS、Samba、Windows文件夹，通过cifs.mount实现，提供图形化挂载工具）
+ 支持自动挂载空闲分区、U盘以及自动向局域网内部共享（通过Samba实现）
+ 支持单线/多线并发多拨（提升上行带宽，提高从因特网获取家庭文件速度）
+ 支持多拨负载均衡
+ 内置综合DNS解决方案：去广告+国内域名加速解析+ 抗污染 + 速度优选 与PSW、Clash无缝集成
+ 支持DDNS（可以通过域名随时获得家庭路由器IP）
+ 支持SSH远程访问（从因特网连接路由器，传输文件，任意访问内网，端口转发等等，支持ed25519）
+ 提供L2TP over IPSec VPN方案（苹果，安卓手机，Mac，Windows直接使用内置客户端即可接入，与PSW、Clash等分流软件完美集成）
+ 支持远程唤醒（WOL，从因特网连入路由器启动家中电脑）
+ 支持定时唤醒（Time WOL，定时启动家庭设备，配合自动关机实现定时运行）
+ 支持全功能Docker，可自由扩展功能（可安装目前还没有移植到OpenWrt上的软件）
+ 支持SFTP（可通过常见SSH客户端随意向路由传输文件，而不需要通过Web界面）
+ 预置虚拟化Agent（优化在虚拟化环境中运行速度，默认OpenVMTools，以软件包形式提供QEMU Agent）
+ 支持网络访问管控（基于MAC黑白名单，按访问网站地址，按时间段控制）
+ 提供Aria2下载工具（远程或者本地下载普通链接，磁力链，BT等全部主流格式，挂载NAS后可直接下载到NAS）
+ 支持SQM 与 NFT Table QOS
+ 提供视觉效果较好的原创主题infinityfreedom
+ 其他必备功能（具体请查看固件下载地址中的内置软件截图）

感谢Lean（coolsnowwolf），Lienol，CTCGFW等等作者。

============================================================================

## 编译说明

注意：
1. **不**要用 **root** 用户 git 和编译！！！
2. 国内用户编译前最好准备好梯子
3. 默认登陆IP 192.168.1.1, 密码 password


编译前：
1. 首先装好 Ubuntu 64bit，推荐  Ubuntu 18 LTS x64
2. 至少30G空闲硬盘空间
3. 2G以上内存，建议4G

编译时:
1. 更新apt-get包信息，命令行输入
`sudo apt-get update`

2. 安装编译依赖包，命令行输入
`sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3.5 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget curl swig rsync`
3. `git clone https://github.com/xiaoqingfengATGH/HomeLede.git HomeLede`命令下载好源代码，然后 `cd HomeLede` 进入目录

4. `git checkout -b k5 origin/k5`

5.  `./prepareCompile.sh`

6. `make download V=s` 下载dl库（国内请尽量全局科学上网,如果程序下载失败，也可以提取网址自行下载后放入dl文件夹，此文件夹通常不需要删除）

7. `make menuconfig`  配置软件包

8. `make -j1 V=s` （-j1 后面是线程数。第一次编译推荐用单线程，国内请尽量全局科学上网）即可开始编译你要的固件了。

编译成功后，再次编译可以启动多线程编译。如4核心8线程i7上开启16线程使用`make -j16 V=sc`

## 固件下载
如需直接编译完成的固件，请访问Google网盘

链接：https://drive.google.com/open?id=1iUDsgh1y5qouP48V61aTsswi3IekscKk

## 交流
* [电报群](https://t.me/t_homelede)
* [QQ群1：1030484865](https://jq.qq.com/?_wv=1027&k=PtlQp9Z9)
* [QQ群2：807741215](https://jq.qq.com/?_wv=1027&k=z9phzgtx)
* [QQ群3：1001944162](https://jq.qq.com/?_wv=1027&k=gEADVcI5)

## Stargazers over time

[![Stargazers over time](https://starchart.cc/xiaoqingfengATGH/HomeLede.svg)](https://starchart.cc/xiaoqingfengATGH/HomeLede)
