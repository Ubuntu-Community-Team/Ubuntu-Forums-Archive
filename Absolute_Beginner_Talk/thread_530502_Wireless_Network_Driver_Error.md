---
title: "Wireless Network Driver Error"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-08-20
payton@the-desktop:/usr/local/src/ndiswrapper-1.47$ cd /usr/local/src/Drivers
    payton@the-desktop:/usr/local/src/Drivers$ ls
    WUSB54GS.cat  WUSB54GS.inf  WUSB54GSv2.cat  WUSB54GSv2.inf
    payton@the-desktop:/usr/local/src/Drivers$ cd
    payton@the-desktop:~$ ndiswrapper -v
    utils version: '1.9', utils version needed by module: '1.9'
    module details:
    filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
    version:        1.47
    vermagic:       2.6.20-15-generic SMP mod_unload 586 
    payton@the-desktop:~$ cd /usr/local/src/Drivers
    payton@the-desktop:/usr/local/src/Drivers$ sudo ndiswrapper -i WUSB54GSv2.inf
    installing wusb54gsv2 ...
    [FONT=Times]couldn't find SourceDisksFiles section - continuing anyway

What am I doing wrong?
I installed ndiswrapper properly, everything prior was running smoothly, but when I try to install the drivers...that happens.[/FONT]

---

### Post by pgar23 on 2007-08-20
I'm assuming no one has an anwer to this problem. Is this a bug or glitch possibly?

---

