## 2024.12.24更新:
- https://youtu.be/5-eSqP-iNnc?si=y_btQcxrX42Ko7nQ

视频19:18秒,解释ad新版本安装中文包bug解决办法

---

# 系统-软件包下
上传安装AdGuardHome时，若提示/etc/crontabs/root no such dirctory，输入mkdir -p /etc/crontabs即可

root检测文件地址:

-     /etc/init.d/AdGuardHome status/restart/stop/start
                （服务名称）  （控制命令）

指定服务重启命令

reboot  系统重启命令

# 配置定时任务:
-     vim /etc/contabs/root

-     50 5 * * * [ -f /usr/bin/AdGuardHome/data/querylog.json.1 ] && rm /usr/bin/AdGuardHome/data/querylog.json.1
      每天五点五十分检测是否有querylog.json.1文件，有则删除

-     cd /usr/bin/AdGuardHome/data
      为打开adguardhome数据文件夹。

# AdgrardHome:
工作目录不要修改到临时目录文件夹下，每次重启会消失

（初次设置需更新核心版本，刚才让先开渠道是为了防止获取核心版本失败

更新完后点击启用，重定向暂时先不用开启）

## 初始化界面
80端口改成8008（个人习惯更改），53端口（Dnsmasq默认占用端口）改为5335（个人习惯）

设置账号密码后一直下一步进入后台主界面即可。

## 设置-常规设置
常规设置下除了使用过滤器之外其余全部取消

## 日志配置
勾选启用日志，时长建议24小时/7天或自行设置，若没有更改位置则建议关闭或24小时以下。

## 统计配置
勾选启用统计数据，时长建议24小时或7天，太长会占用存储空间

## 设置-DNS设置
上游服务器首先默认不要动，选择并行请求

bootstrap输入自己光猫后台测试过的两个dns即可

延迟低的写在第一个/或者写自己网上查询的延迟低的dns，其余取消。

## DNS服务配置
速度限制改为0，勾选启用EDNS客户端子网、启用DNSSEC、禁用IPv6地址的解析

## DNS缓存配置
缓存大小根据自己设备缓存容量设置即可，默认4M

勾选乐观缓存

其余设置默认即可

## 过滤器-黑名单
删除默认的两个，自行添加规则即可

广告终结者
- http://sub.adtchrome.com/adt-chinalist-easylist.txt

EasyListChina
- https://easylist-downloads.adblockplus.org/easylistchina.txt

Anti-AD
- https://raw.githubusercontent.com/privacy-protection-tools/anti-AD/master/anti-ad-easylist.txt

屏蔽cookies相关的警告
- https://www.i-dont-care-about-cookies.eu/abp/

秋风广告
- https://raw.githubusercontent.com/TG-Twilight/AWAvenue-Ads-Rule/main/AWAvenue-Ads-Rule.txt

百万ADH广告拦截过滤规则
- https://raw.githubusercontent.com/BlueSkyXN/AdGuardHomeRules/master/all.txt


## 彻底配置完后
上游服务器输入127.0.0.1:7874

（此为openclash的默认端口，在openclash的系统设置里面查看）

（此时测试上游可能失败，不用管）

此时回到设备后台选择作为dnsmasq的上游服务器就可以使用了