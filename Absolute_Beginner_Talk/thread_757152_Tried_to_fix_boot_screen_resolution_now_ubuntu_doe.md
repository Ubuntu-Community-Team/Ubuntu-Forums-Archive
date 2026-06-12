---
title: "Tried to fix boot screen resolution now ubuntu doesn't load..."
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by outta_control on 2008-04-16
I installed Ubuntu on a hp media center computer. Ubuntu dual boots with windows. The computer has a 140 gigabyte hard drive and I created a 13 gig partition for Ubuntu. It worked great, however, I had a small issue. Every time the computer would boot up or shut down, there was an error message that said "display setting out of range, change resolution to 1280 x 1024 at 60 hz." So i followed this link and tried to fix it.

[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

I followed the instructions to the best of my knowledge and rebooted the computer. Grub came up and I selected Ubuntu. Then, the screen went black and the splash screen never showed up. Sadly, Ubuntu didn't load up either. Please does someone know an easy fix to this problem? Ubuntu seems great and I really want to get a feel for it and use it.

p.s. I tried loading in rescue mode or the second option in grub. It said however, [COLOR="Red"]Alert! /dev/disk/by-uuid/3aaa9316-0ced-46aa-bbe0-c32d2919333b does not exist. Dropping to a shell.[/COLOR]

---

### Post by whouseswindowsanyway on 2008-04-16
ok try this -- im not too sure if it will help you but it might -- 

when ubuntu finishes loading up pres CTRL+ALT+F1

then do the following : 

1)cd /etc/X11
2)ls -lrt xorg*

now look in those for the backups you have should show something like this : 

date  xorg.conf
date  xorg.conf.1
date  xorg.conf.2

now in all those xorg.conf files check for the newest one that you have (except for the normal xorg.conf file -- because that one is broken -- or atleast thats what i think) 
then let's say it is xorg.conf.2

do the following : 
sudo cp xorg.conf.2 xorg.conf

then enter your password
then press CTRL+ALT+F7
then press CTRL+ALT+BACKSPACE

-that should work -- i Think?

If it doesn't sorry -- im pretty new to this....

---

### Post by outta_control on 2008-04-16
> **whouseswindowsanyway said:**
> ok try this -- im not too sure if it will help you but it might -- 

when ubuntu finishes loading up pres CTRL+ALT+F1

then do the following : 

1)cd /etc/X11
2)ls -lrt xorg*

now look in those for the backups you have should show something like this : 

date  xorg.conf
date  xorg.conf.1
date  xorg.conf.2

now in all those xorg.conf files check for the newest one that you have (except for the normal xorg.conf file -- because that one is broken -- or atleast thats what i think) 
then let's say it is xorg.conf.2

do the following : 
sudo cp xorg.conf.2 xorg.conf

then enter your password
then press CTRL+ALT+F7
then press CTRL+ALT+BACKSPACE

-that should work -- i Think?

If it doesn't sorry -- im pretty new to this....


Thanks for replying. I just have one question. You said boot up Ubuntu. The problem is that it's not booting up. Or at least I can't see it. What do I boot up to do that? The live cd? The recovery? The shell? Sorry I'm pretty new at this.

---

### Post by outta_control on 2008-04-16
I entered the recovery mode (the second choice in grub), however, before it fully loads this error message comes up. 
[COLOR="Red"]Alert! /dev/disk/by-uuid/3aaa9316-0ced-46aa-bbe0-c32d2919333b does not exist. Dropping to a shell.[/COLOR]

Does anyone know how to fix this? I really want ubuntu to work again.

---

