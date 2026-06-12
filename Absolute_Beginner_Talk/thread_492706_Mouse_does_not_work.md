---
title: "Mouse does not work"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Neo_XY on 2007-07-05
I just finished installing the Ubuntu today afternoon on a Virtual PC 2007, I had a little problem with logon screen first, but it was fix by changing the 24 to 16 on DefaultDepth (xorg.conf).
Then I restarted the again, the screen was fixed, I was able to login, but now the mouse is not working at all. How do I fix the mouse issue?

N.

---

### Post by davidjmayo on 2007-07-05
[Ctrl} + [Alt] + [Print Screen Sys Rq]

If that doesn't work pull the mouse connection out of the computer, wait a couple of secs and plug in back in (works for a PS/2 mouse but I think I read somewhere it shouldn't be used for a USB mouse)

---

### Post by gaylapdancer on 2007-07-05
It happened with me in OpenSuSE 10.2 and it was a common problem for my type of pc (Dell Dimension E521) and is something to do with my motherboard. I found the only solution was to unplug my mouse then plug it in again (USB mouse) But as it was so frequent and annoying, I switched to Ubuntu and haven't had problems since :D

---

### Post by mzmiric5 on 2007-08-28
No it is the problem with VPC2007, and here is the solution:
Hit CTRL-ALT-F1 to drop to a console and log in.
Type sudo nano /boot/grub/menu.lst.
Press CTRL W and type end default options, then press Enter.
The first entry in the list below is the entry containing the information to boot Ubuntu in regular mode.  Find the line that starts with kernel and go all the way to the end of it.  At the end, type i8042.noloop, press CTRL O, and press Enter to save.
At this point, you can do the same with the other entries, like the recovery mode one if you care enough to bother.  If not, just hit CTRL X to exit nano.
Type sudo reboot to reboot the VM. 
The next time you boot into XWindows, your mouse should work without issue.  (You should also note that if you happen to upgrade your kernel version, you'll need to make this change *again*.)

---

