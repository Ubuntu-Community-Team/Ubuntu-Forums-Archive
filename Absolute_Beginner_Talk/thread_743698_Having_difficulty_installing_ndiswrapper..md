---
title: "Having difficulty installing ndiswrapper."
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by tmskraus on 2008-04-02
So here are the instructions I am following -- they come from the ndiswrapper file itself (INSTALL): [http://pastebin.com/m79748fda](http://pastebin.com/m79748fda)

I can do make uninstall, but make gives me this: 
[http://pastebin.com/m2d2f4f12](http://pastebin.com/m2d2f4f12)

I've been able to make the wireless connection work just fine using these instructions in the past, but I didn't get all those errors the first time. What am I doing wrong? I heard I have to  ./config something, maybe? 

Here is my wireless driver: 

> 03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
 

Please help. :(

---

### Post by tmskraus on 2008-04-02
Okay, everything has worked now except the final step - "modprobe ndiswrapper" 

This is the error: 
> FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

---

### Post by tmskraus on 2008-04-02
Okay, nevermind, I've gotten it to work now. =D

---

### Post by chris82543 on 2008-04-02
I tried using those directions to install ndiswrapper and found them hard to follow but I thought these directions from the ndiswrapper site to be easier to be a bit better [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/") and there are alot of resorces that can help you if you get stuck. Good Luck!!!

---

