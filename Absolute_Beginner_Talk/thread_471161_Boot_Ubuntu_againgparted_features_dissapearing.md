---
title: "Boot Ubuntu again?/gparted features dissapearing?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-06-11
I just installed windows xp (forgive me :p) and I already had ubuntu installed.  We all know that windows being windows would not wait to see if it's ok to re-write the MBR, and so now it only boots windows.  No problem here, I can use the live CD temporarily, like now, but I would like to know how to get it booting again!  The way I see it, there are two options:
1. use the windows boot loader (C:\boot.ini) to load ubuntu and windows
2. somehow re-write the master boot record to use grub and then load ubuntu and windows

Anyone know how to do either one of these?

---

### Post by HackingYodel on 2007-06-11
***Disclaimer***  I haven't used/dual booted Windows for a couple years now.  Always use cations when messing about in your MBR   ***Disclaimer***

If you can use Windows to boot into Ubuntu, just issue the **sudo grub-install *install device*** command in a terminal.  On my laptop ***install device*** is /dev/sda and on the desktop it's /dev/hdb, (issue a **mount** command and look where / is mounted but do NOT use /dev/hda1 instead of just /dev/hda or /dev/sda1 instead of /dev/sda, etc..)  This will install grub to your MBR.  Look in /boot/grub/menu.lst on Ubuntu for the grub menu configurations.

You can also **man grub-install** or **info grub-install** in Ubuntu for the nitty-gritty. 

Sorry I can't remember more, it has been a while, but I think this will work for you.  Again, be careful with the MBR.

Good luck and I hope this helps you.

---

### Post by ryanVickers on 2007-06-11
Ok, thanks for the tip.  Actually while I was away from the internet, I found this other little tool that makes it really easy to configure and recover the MBR using grub or other things!  I *think* the MBR is working fine, I can even boot my windows or options of linux, but when I try to boot linux, it says domething like:
> error 17: cannot mount selected partition

I know it actually is mountable, so I'm thinking it's trying to mount something other than what it's supposed to for some reason - by the way, I checked in the fstab and mtab and they are setup correctly!

---

### Post by ryanVickers on 2007-06-11
I fixed it!  I noticed in the blah/menu.lst it was looking under (hd0,1) (my windows partition) for the linux boot stuff, so I changed them all to 0,0 and now all linux and windows boots great!  Hooray!

---

