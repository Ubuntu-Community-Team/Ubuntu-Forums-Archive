---
title: "couldn't find SourceDisksFiles section - continuing anyway..."
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
I installed ndiswrapper properly, everything prior was running smoothly, but when I try to install the drivers...that happens.

ps. (for ubuntuforums.org admin)  When I put the title of this post in the section, it says database error, and I tried all of the listed solutions but it keeps happening. Just an FYI.


[/FONT]

---

### Post by pgar23 on 2007-08-20
should I install the .cat file first?

---

### Post by pgar23 on 2007-08-20
Is there a soulution to my dilema?

---

### Post by pgar23 on 2007-08-20
bump......?

---

### Post by pgar23 on 2007-08-20
Bump-i-dee-doo-da........?

---

### Post by pgar23 on 2007-08-20
I thought forums were created to help people with technical(and non technical/newb) difficulties.

---

### Post by merlin666 on 2007-09-07
I am having the same problem with netbc564.inf ... keeps installing the dreaded bcm43xx instead.

---

### Post by darklordveynom on 2007-12-20
I'm having the exact same problem.

---

