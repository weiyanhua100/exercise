=======================
路由器练习题1 - 路由器基础
=======================

1. 找到VM1对应的port
===================

命令
----

    nova list
    neutron port-list --device-id <vm uuid>

2. 查找虚机对应的网卡
==================

命令
----

    ip a | grep <port uuid前8个字节>

找到虚机对应的tap设备，设备命名应该是tap<port uuid前8个字节>

3. 监听虚机的tap设备
==================

命令
----

    sudo tcpdump -nei <步骤2中找到的虚机网卡名>

4. 从horizon界面登录虚机VM1
=========================

参考视频步骤

5. 在VM1内pingDHCP地址
=====================

在步骤4的窗口

命令
----
    ping 11.0.0.2

6. 查看tap设备抓到的包
====================

回到步骤3窗口，查看tcpdump抓到的包。

7. 在VM1内ping一个其他网络地址
===========================

回到步骤5的窗口

命令
----

    ping 20.0.0.10

8. 查看tap设备抓到的包
====================

回到步骤6窗口

查看tcpdump抓到的包，并分析为什么会抓到这样的包？

9. 删除VM1默认路由
================

回到步骤7窗口

命令
----
    sudo ip r del default

10. 在VM1内ping一个其他网络地址
============================

命令
----
    ping 20.0.0.10

ping直接失败了，分析为什么会出现这个结果？

11. 恢复VM1默认路由
=================

    sudo ip r add default via 11.0.0.1
