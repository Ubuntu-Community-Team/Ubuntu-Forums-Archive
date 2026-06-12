---
title: "win xp not booting"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-07-19
I cannot boot up xp on the rare occasions I need it. I have put this into terminal 
gksudo gedit /boot/grub/menu.lst
and at the end of the resulting info I get this:

This entry automatically added by the Debian installer for a non-linux OS
on /dev/hdb1
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Any comments?


title Windows Vista
root (hd0,1)
makeactive
chainloader +1

---

### Post by alienexplorers on 2007-07-19
Are you running both Vista and XP/NT/2000.  The boot loader can be confused by this setup.  I have seen fixes in the forum.  Try searching for information.

---

### Post by jasonlfunk on 2007-07-19
My guess is that your root partition is wrong. What happens when you select WinXP from GRUB? You might want to try messing around with different values for the root to see if you can figure out which one it is. My guess is (hd1,1).

---

### Post by Benbow on 2007-07-19
I don't know where the Vista came from, I don't have it, just xp!

---

### Post by Benbow on 2007-07-19
Can you explain how I rewrite the boot file to hd1,1 and then install it. I really am a raw beginner with terminal.

---

