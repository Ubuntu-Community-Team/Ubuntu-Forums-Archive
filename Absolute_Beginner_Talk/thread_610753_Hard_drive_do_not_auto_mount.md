---
title: "Hard drive do not auto mount"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by i_love_it on 2007-11-12
Hi guy.
I have a dual-boot computer XP and Ubuntu 7.10. It perform just well, and Ubuntu manage to correctly automount my XP partition. However, after I perform a ghost clone with my C driver, i can still boot both OS but Ubuntu no longer automount my C driver. I have to manually mount it. And it is not shown as "sda1" like before, but with a different name "disk".
Anyone can show me how to fix that problem?
Thank you in advance

---

### Post by overdrank on 2007-11-12
> **i_love_it said:**
> Hi guy.
I have a dual-boot computer XP and Ubuntu 7.10. It perform just well, and Ubuntu manage to correctly automount my XP partition. However, after I perform a ghost clone with my C driver, i can still boot both OS but Ubuntu no longer automount my C driver. I have to manually mount it. And it is not shown as "sda1" like before, but with a different name "disk".
Anyone can show me how to fix that problem?
Thank you in advance

Hi maybe this link can help
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Automatically](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Automatically)
Good luck!

---

### Post by ajgreeny on 2007-11-12
> Hi maybe this link can help
[http://ubuntuguide.org/wiki/Ubuntu:G..._Automatically]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Automatically")
Good luck!Surely thats only where you have shared folders over a samba share?  It seems more likely to me that the disk UUID has changed since you used the ghost clone of windows.  Look at the UUID of the windows partition using ```
ls -l /dev/disk/by-uuid
```and check that it is the same as your etc/fstab file.  If not edit the fstab to be the same and then windows should automount as before.

Alternatively you can forget about the UUID completely and just use the sda1 (or whatever it is where windows is installed.)

---

### Post by i_love_it on 2007-11-12
@ajgreeny : Thanks man. That's really help.
@overdrank: It did not help, but thanks for trying and for the quick reply

---

