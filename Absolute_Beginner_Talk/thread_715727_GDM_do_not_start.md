---
title: "GDM do not start"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by bilacus on 2008-03-05
I'm running Gutsy 64 bit on my desktop,.... I was really happy

Last month I try to install a mac4lin theme and icons and awn bar the only things I could change
were the icons set and windows borders, and I did like them a lot.
At the reboot I found the surprise! after the choice of the kernel vertion the screen remains black whith a a cursor flashing on the up-left corner. and nothing else happen.

I'm completely lost....

---

### Post by bilacus on 2008-03-05
up

---

### Post by erginemr on 2008-03-05
Hard to say, it can be a thousand of things which may cause this problem...

What happens when you select the second item (recovery mode) in the Grub menu. In this mode, the system will try to boot in to a text only environment with root permissions. Do you happen to receive any error mesage before the computer stalls?

---

### Post by bilacus on 2008-03-05
I have this:     GDM .........   [fail]

I try  root>gdmsetup         it say libgtk2.0.X11.so.0 or something like ( at the moment I'm not at home)
can't find share libraries  but this lib exist if I remember in /usr/lib.

I run also sudo ```
dpkg-reconfigure xserver-xorg
```   but did not help

---

### Post by erginemr on 2008-03-05
OK. Two similar threads for you (and me) to read:
[http://ubuntuforums.org/showthread.php?t=204974](http://ubuntuforums.org/showthread.php?t=204974)
[http://ubuntuforums.org/showthread.php?t=669672](http://ubuntuforums.org/showthread.php?t=669672)

Besides, do you know if you will have access to the internet when at the recovery mode? I hope so, because you may need to install a secondary login manager such as "xdm" as a transient alternative to "gdm".

EDIT: Doing a search in the forum with keywords **"gdm symbol lookup error" **also yield a bunch of threads.

---

