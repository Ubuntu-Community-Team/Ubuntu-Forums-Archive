---
title: "defunctional keyboard on MacBook c2d 2,16"
date: 2007-06-09
forum: Apple Intel Users
---

### Post by pveith on 2007-06-09
Hi all,

yesterday my brand new macbook arrived and i imediately started installin ubuntu on it. all went find had wireless and all basic things working. Started changing the keyboard using xmodmap (for security only for my user). Last thing i did was updateing  kernel update.

Today the macbook seems to run, but i cont use the keybord (touchbad etc. works). I even cant use a usb-keyboard i attach...

Arg, any suggestions what can be done to diagnose this one?

---

### Post by pveith on 2007-06-09
Arg, i even forgot to install sshd. Cr*p. I can work with the ubuntu live-cd though. Keybord works there...

Oh and i can't even press escape and select a different kernel on grub...

---

### Post by kzm. on 2007-06-09
which ubuntu you installed? 32 or 64bit?

---

### Post by ronocdh on 2007-06-09
> **kzm. said:**
> which ubuntu you installed? 32 or 64bit?
I don't know how this would affect anything, but I'm interested to know where you were going with it, kzm. Anyway, pveith, have you tried booting from the live CD and **chroot**ing into your on-disk installation and changing back your xmodmap?

---

### Post by pveith on 2007-06-10
Right now i am having problems with the live-cd, too. Also no keyboard. Arg. i will try 32-Bit then.

will be right back after the test. [Edit: just tried 64Bit again with the bootoption lpj]

[Edit] Pressing no keys during the startup seems to fix the no-keyboard problem with the 64 live-cd (did not help with the installed ubuntu) . Additionally i don't think that my xmodmap could affect the system as it is only loaded after login in gdm. And as i can't login it is not used at all.

Another thing i was thinking about is the lpj=8000000 option. As i am using a 2,16 C2D it should be lpj=8640000, or not?

Patrick
P.S.:Yesterday i had to leave, so i was not abel to comment on this.Sorry!

---

### Post by pveith on 2007-06-10
I found that there are others with problems with keyboard, who are not using Ubuntu. It even happens in grub to me and unfortunately this is caried on to my X Session...

---

### Post by pveith on 2007-06-10
Finally some light is shed on the issue. I forgot that i tried to change the fn-key-behaviour using a modprobe.d entry, but didn't restart to test it, not to mention that i completely forgot about that one...

Does anyone have a working solution to change the fn-key behaviour? Currently F-Keys behave like fn is pressed.

---

### Post by Movi on 2007-06-10
Yes, apt-get install sysfsutils, then nano /etc/sysfs.conf. In that file at the bottom put
 
module/hid/parameters/pb_fnmode = 2

This will make the F-keys work as normal, and with pressing Fn it will make the key do the functions (like volume control)

---

### Post by pveith on 2007-06-10
cool thanx, works like a charm.

---

### Post by kzm. on 2007-06-10
about the 32 - 64bit question.. that was a selfish question, because i can t get the wifi work and was wondering, if its because i installed the 64bit version.

---

### Post by pveith on 2007-06-10
Okay then i can confirm that madwifi works with 7.04 64Bit. Everything now smooth...

---

