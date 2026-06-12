---
title: "Wireless problem"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by oconnellmm on 2005-08-08
I just installed Ubuntu on my work computer and liked it so much i decided to put it on my home computer.

At work i use a direct ethernet connection, but at home i use a linksys wireless b access point and linksys wmp11 wireless b pci adapter.  When i enter into the network settings and under connections tab i can see modem and ethernet but do not see anything for wireless.  

I have searched the ubuntulinux.org site and seems like there are lots of different ways to go about getting on a wireless network.  I was wondering if anyone has a clear cut way that worked without any problems.

---

### Post by KingBahamut on 2005-08-08
[http://ubuntuforums.org/archive/index.php/t-7319.html](http://ubuntuforums.org/archive/index.php/t-7319.html)

Hope this helps a little

for a Non-Ubuntu Look into wireless networking, read here. 
[http://www.linuxhomenetworking.com/linux-hn/wmp11-linux.htm](http://www.linuxhomenetworking.com/linux-hn/wmp11-linux.htm)

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=oconnellmm]
I have searched the ubuntulinux.org site and seems like there are lots of different ways to go about getting on a wireless network.  I was wondering if anyone has a clear cut way that worked without any problems.[/QUOTE]

Actually, if it doesn't work there is only way way usually. ndiswrapper:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

### Post by oconnellmm on 2005-08-09
i have tried almost everything that was listed on all those forums and i am still not getting past installing the .inf files.  I am going to retrace exactly what i did and errors that i am getting.

1. installed ndiswrapper-utils and ndiswrapper-source from synaptic package manager

2.downloaded the drivers for my wmp11_v4 and stored them under /home/oconnellmm

3.this is what is in that directory
> root@oconnellmm:/home/oconnellmm # ls
AutoRun      dl            LSIPNDS.inf   ndiswrapper-1.1  WMP11NDS.cat
AUTORUN.INF  lsbcmnds.cat  LSIPNDS.sys   SETUP.EXE        WMP11NDS.inf
bcmwl5.sys   lsbcmnds.inf  LSIPNDSX.sys  Utility          WMP11NDS.sys
Desktop      LSIPNDS.cat   music         windows_drivers 

4.when i go to try and install any .inf files i get this message
> root@oconnellmm:/home/oconnellmm # sudo ndiswrapper -i lsipnds.inf
Installing lsipnds
cp: cannot stat `lsipnds.inf': No such file or directory 

i get this message with all of the .inf files that i am trying to install.  i am prob doing something really dumb, but i am really frustrated at this point

---

### Post by oconnellmm on 2005-08-09
figured it out talked to someone here at work and he told me the files were all case sensative, that is where i was going wrong.

---

### Post by dabeej on 2005-08-17
Anyone using a WMP11 v4 got their Link Quality showing correctly. Would be nice to have that. Also to be able to use the stats would be nice too. =/

---

