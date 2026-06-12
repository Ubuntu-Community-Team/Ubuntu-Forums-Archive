---
title: "No Screens Found"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by ddover on 2007-03-08
I appreciate your help in advance.

I just did a new install on a
Compaq DeskPro PII 300
64 megs RAM, 
6.5 gig hard drive, 
1.44 floppy drive, 
No CD-ROM drive, 
10/100 embedded Intelligent ethernet
onboard S3 Virge graphics controller
Ubuntu 6.06

Installation was a hassle with no CD drive but I finally made it work

Problem is when I start up the computer it loads ubuntu and then has a server x error
"No screens found"

It then has a whole lot of detailed information.

If anyone could tell me how to transfer the log file of this info to a floppy (or better yet a USB drive) I would be happy to post it. I look forward to my first linux expereince and am already a fan of the large helpful community. Please let me know if I can provide any more information.

Thanks,
ddover

---

### Post by taurus on 2007-03-08
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```

p.s.  64MB of RAM and running Gnome, eh!

---

