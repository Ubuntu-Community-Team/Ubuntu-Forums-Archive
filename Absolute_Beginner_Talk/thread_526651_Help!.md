---
title: "Help!"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by ModularMike on 2007-08-15
While using this how-to: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29) to install my USB network adapter, I ran into these errors on step 5 :
```
mike@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65:42: error: invalid suffix "c0026" on integer constant
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:163: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘->’ token
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:213:2: error: #endif without #if
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2088: warning: unused variable ‘device’
make[2]: *** [/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
mike@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ 

```

I didn't even edit that file but I would like to know where these errors are in the file so I can attempt to fix it, ANY help would be appreciated. Thanks.

---

### Post by ddrichardson on 2007-08-16
The error that's stopping the show is at line 163 in /home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c it looks like a missing line terminator ";"

---

