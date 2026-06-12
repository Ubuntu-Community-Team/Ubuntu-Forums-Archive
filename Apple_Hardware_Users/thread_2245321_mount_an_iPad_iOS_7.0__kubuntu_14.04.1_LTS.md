---
title: "mount an iPad iOS 7.0 / kubuntu 14.04.1 LTS"
date: 2014-09-22
forum: Apple Hardware Users
---

### Post by darko5 on 2014-09-22
Hey !


I'm trying to mount my girlfriend's iPad on my computer.

When I connect the iPad, a get a message asking me if I trust this computer on the iPad screen, just one time. I click on ok "trust" and the message disappear.

My problem : the iPad doesn't seem to be mounted properly, or at least I don't get access to most of the folders. I get a message like "available camera" on the "taskbar", that allows me to access the iPad picture folder, but nothing else.

The libimobiledevice pacage is installed by default, I got the repositories version :
```
darko@eos:~$ apt-cache showpkg libimobiledevice4
Package: libimobiledevice4
Versions: 
1.1.5+git20140313.bafe6a9e-0ubuntu1
```


The iPad doesn't show in the sfdisk and df commands feedback :

```
darko@eos:~$ sudo sfdisk -l
[sudo] password for darko: 


Disk /dev/sda: 15566 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0


   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   1867-   1868-  14998528   83  Linux
/dev/sda2       1867+  15566-  13699- 110033921    5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       1867+   2738-    872-   6999040   83  Linux
/dev/sda6      14072+  15566-   1494-  11999232   82  Linux swap / Solaris
/dev/sda7       2738+  14071-  11334-  91032576   83  Linux

```


```
darko@eos:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1       14631856 6248036   7617512  46% /
none                   4       0         4   0% /sys/fs/cgroup
udev             3920752       4   3920748   1% /dev
tmpfs             787128    1212    785916   1% /run
none                5120       0      5120   0% /run/lock
none             3935628   48676   3886952   2% /run/shm
none              102400      20    102380   1% /run/user
/dev/sda5        6757952 2631956   3759660  42% /home
/dev/sda7       89472192 5445756  79458424   7% /data

```

However, I get this for lsusb, referring to the iPad
```
darko@eos:~$ lsusb 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2db Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 005: ID 17ef:6045 Lenovo 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 05ac:12a6 Apple, Inc. iPad 3 (3G, 16 GB)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

What do you guys think, what should I try to gain access to all the folders in the iPad, and not only to the picture folders ?

---

### Post by darko5 on 2014-09-24
I tried this fix : [http://www.omgubuntu.co.uk/2014/03/ios7-ipad-iphone-ubuntu-trust](http://www.omgubuntu.co.uk/2014/03/ios7-ipad-iphone-ubuntu-trust) but it didn't work. Actually I "can't" uninstall the [COLOR=#000000][FONT=Arial]libimobiledevice4_[/FONT][/COLOR]1.1.5 version from the regular repositories without uninstalling quite a few other packages 
> darko@eos:~$ sudo apt-get remove libimobiledevice4[sudo] password for darko: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  amarok amarok-utils libgpod-common libgpod4 libimobiledevice-utils
  libimobiledevice4 upower
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 27,9 MB disk space will be freed.
Do you want to continue? [Y/n]
So I installed the 2_1.1.6 version without uninstalling the [COLOR=#000000][FONT=Arial]4_1.1.5 one, and well, nothing changes. How could I tell the program that mount the iPad to use the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]2_1.1.6 library, what do you think ?[/FONT][/COLOR]

---

