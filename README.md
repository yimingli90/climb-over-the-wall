# 快速搭建 Shadowsocks 翻墙教程
#### ● 服务器：阿里云 ECS服务器
#### ● 系统：Ubuntu 20.04 64位 / Debian 10.11 64位
## 一、注册阿里云账号并实名
　　[https://www.aliyun.com/](https://www.aliyun.com/)
## 二、购买服务器并配置弹性公网IP
### （一）购买服务器 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/README_picture/01.md)
　　　● 先前往购买页 <br/>
   　　**1. 基础配置** <br/>
　　　（1）自定义购买 → 包年包月 → 中国(香港) → 可用区C <br/>
　　　（2）实例规格选择“1vCPU 0.5GiB”的“突发性能实例 t5” <br/>
　　　（3）镜像选择“公共镜像”的“Ubuntu 20.04 64位”或者“Debian 10.11 64位”（这一步非常重要，不要选错了） <br/>
　　　（4）系统盘选择“高效云盘”，容量调整为“20G” <br/>
　　　（5）购买时长选择“1周”，可以先试试看 <br/>
　　　（6）点击“下一步：网络和安全组” <br/>
   　　**2. 网络和安全组** <br/>
　　　（1）取消“分配公网IPv4地址”，其余选项默认 <br/>
　　　（2）点击“下一步：系统配置” <br/>
   　　**3. 系统配置** <br/>
　　　（1）选择“自定义密码”，并设置密码 <br/>
　　　（2）点击“确认定单” <br/>
   　　**4. 确认定单** <br/>
　　　（1）点击“确认下单” <br/>
　　　（2）支付成功 <br/>
　　　（2）点击“管理控制台” <br/>
   　　_**服务器购买完毕，下配置弹性公网IP**_ <br/>
### （二）购买弹性公网IP [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/README_picture/02.md)
　　　● 先前往购买页 <br/>
　　　（1）按量付费 → 中国(香港) → BGP(多线)-精品 <br/>
　　　（2）选择“按使用流量计费” <br/>
　　　（3）“带宽峰值”拉满至“200Mbps” <br/>
　　　（4）点击“立即购买” <br/>
　　　（5）选择“我已阅读并同意弹性公网IP开通服务协议” <br/>
　　　（6）点击“立即开通” <br/>
   　　_**弹性公网IP购买完毕，下将弹性公网IP绑定到服务器上**_ <br/>
### （三）将弹性公网IP绑定到服务器 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/README_picture/03.md)
　　　● 先返回实例列表界面 <br/>
　　　（1）点击图中所示 <br/>
　　　（2）点击“确定” <br/>
   　　_**弹性公网IP绑定完毕，下配置服务器**_ <br/>
## 三、服务器端配置
### （一）配置服务器 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/README_picture/04.md)
　　　● 先返回实例列表界面 <br/>
   　　**1. 进入服务器** <br/>
　　　（1）远程连接 → 立即登录 <br/>
　　　（2）输入刚才设置的密码 → 确定 <br/>
　　　（3）显示此界面表示已成功进入服务器 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/picture/28.png) <br/>
   　　**2. 配置服务器** <br/>
　　　（1）输入以下命令检查更新 <br/>
　　　　　　`apt update` <br/>
　　　（2）输入以下命令安装 Shadowsocks <br/>
　　　　　　`apt install -y shadowsocks-libev` <br/>
　　　（3）输入以下命令修改 Shadowsocks 的配置文件 <br/>
　　　　　　`vi /etc/shadowsocks-libev/config.json` <br/>
　　　　　　回车后，出现如图所示 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/picture/29.png) <br/>
　　　　　　在英文输入法环境下，在键盘上按一下“**i**”键，左下角发生变化，变为“--INSERT--” [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/picture/30.png) <br/>
　　　　　　说明此时已**进入**编辑模式，可修改文件 <br/>
　　　　　　将第 1 行改为如下： <br/>
　　　　　　`"server":"0.0.0.0",` [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/picture/31.png) <br/>
　　　　　　第 5 行中 “:" 右边引号内的内容为默认密码，可改成你自己喜欢的，也可不改，其余行保持不变 <br/>
　　　　　　此时，拍一下照或截一下屏，之后会用到 <br/>
　　　　　　在键盘上按一下“**Ecs**”键，左下角“--INSERT--”消失，表示**退出**编辑模式 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/picture/32.png) <br/>
　　　　　　在英文输入法环境下，输入以下命令保存修改并退出<br/>
　　　　　　`:wq` [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/picture/33.png) <br/>
　　　　　　回车后即回到原命令行界面 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/picture/34.png) <br/>
　　　（4）输入以下命令重启 Shadowsocks <br/>
　　　　　　`systemctl restart shadowsocks-libev` <br/>
　　　（5）输入以下命令检测 Shadowsocks 是否开始运行<br/>
　　　　　　`systemctl status shadowsocks-libev` <br/>
　　　　　　显示图中内容表示已成功配置 Shadowsocks 并正常运行 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/picture/35.png) <br/>
   　　_**服务器配置完毕，下配置安全组**_ <br/>
### （二）配置安全组 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/README_picture/05.md)
　　　● 先返回实例列表界面 <br/>
　　　（1）进入安全组配置界面 <br/>
　　　（2）点击“添加安全组规则” <br/>
　　　（3）写入内容 <br/>
　　　　　　端口范围：`8388/8388` <br/>
　　　　　　授权对象：`0.0.0.0/0` <br/>
　　　　　　其余内容默认，点击”确定“ <br/>
   　　_**安全组配置完毕，下配置客户端**_ <br/>
## 四、客户端配置 [[点击此处查看图片]](https://github.com/FlorianGu/climb-over-the-wall/blob/main/README_picture/06.md)
　　　至此，服务器端配置已大功告成，客户端配置就简单许多 <br/>
   　　**1. 下载 Shadowsocks 客户端** <br/>
   　　　[https://github.com/shadowsocks/shadowsocks-windows/releases](https://github.com/shadowsocks/shadowsocks-windows/releases) <br/>
   　　**2. 解压后打开文件夹，打开“Shadowsocks.exe”** <br/>
   　　**3. 出现界面后，按刚刚拍照或截屏的内容对应填入界面中** <br/>
   　　_**客户端配置完毕**_ <br/>
### _好啦， Shadowsocks 已成功搭建，快去访问一下 Google 吧！_
[https://www.google.com/](https://www.google.com/)
<br/><br/>
最后，推荐一款可在大陆地区下载并使用的 IPhone/IPad 翻墙软件 **Outline** <br/>
[https://apps.apple.com/cn/app/outline-app/id1356177741](https://apps.apple.com/cn/app/outline-app/id1356177741)<br/><br/>
### 参考文献：
　● [Shadowsocks 官方文档](https://github.com/shadowsocks/shadowsocks-libev#debian--ubuntu)<br/><br/>
_如有任何问题，欢迎[ **Issues** ](https://github.com/FlorianGu/climb-over-the-wall/issues) 或发送邮件 `floriangu2021@gmail.com`_
