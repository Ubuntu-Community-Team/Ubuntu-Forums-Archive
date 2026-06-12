---
title: "Can't boot from Live CD"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Shenkion on 2008-03-01
So I tried to install Kubuntu 7.04, but no luck.  I can get to the Live CD menu, and choose install or start, but once it goes through the boot screen, I get an error message.

BusyBox v1.1.1 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs) [    41.875125] atal.00 failed to set xfermode (err_mask-6x40)

I think that's the message, or at least the general gist of it.
I've installed ubuntu before (dual boot w/ xp)  and had no problems, but I formatted both partitions and wanted to start over.  I tried the same ubuntu disc I used before, and that doesn't work either, so I'm assuming I screwed something up when I formatted.  Any suggestions?

---

### Post by Scarath on 2008-03-01
Try another live CD (e.g. burn a new one)? Try another distro even, like puppylinux or slax, when you boot them up (if they work)  try doing fdisk/cfdisk.

---

### Post by sillyxone on 2008-03-01
can you check again to make sure there is no hardware changes? I got that message twice on two laptops, both was the problem with new SATA controller and I had no solution. 

Try to isolate the problem by unplugging the HDD and boot up to see if you can get pass it.

Try the suggestion here to see if it works for you:
[http://ubuntuforums.org/archive/index.php/t-568449.html](http://ubuntuforums.org/archive/index.php/t-568449.html)

---

### Post by Shenkion on 2008-03-01
Unplugging the hard drive doesn't work.  Still getting the same error.  Also, @ scarath, I've tried several different CDs, none work.  I chose the "check disc for errors" and that gave me the same error message.

---

