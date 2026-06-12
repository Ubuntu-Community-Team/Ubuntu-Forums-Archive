---
title: "can't install from ./makedrv file"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by wlandymore on 2008-01-24
Hi, I am trying to install my wireless USB (ALFA neworks AWUS036H) and I downloaded the file from:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)

then I go to the shell and try to run the makedrv file included but I get some errors after it starts unpacking it.

-------------------
/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053: error: for each function it appears in.)
/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2054:77: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2055:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2056:80: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2057:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function ‘rtl8187_usb_probe’:
/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2956: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
make[2]: *** [/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/will/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
---------------

Can anyone tell me what this is in reference to? I've been looking all over the place and I can't seem to find a way to make it happy and finish the build.

Thanks.

---

