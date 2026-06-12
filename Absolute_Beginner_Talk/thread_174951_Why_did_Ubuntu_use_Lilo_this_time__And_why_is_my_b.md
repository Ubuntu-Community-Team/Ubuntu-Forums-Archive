---
title: "Why did Ubuntu use Lilo this time?  And why is my boot time twice as long?"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by ktownhero on 2006-05-12
I just recently did a fresh install of Breezy Badger after getting a new hard drive, and for some reason the installation seems to be somewhat different.  This is using the same disc that I have used about 3 other times for installation.  In the past, it used Grub as the bootloader, this time it used Lilo.  I liked Grub better because it was graphical.

But, more importantly, it seems like with this installation that there are dozens of other things starting up at bootup that never did in my previous installations.  Things like Bluetooth, which I don't use at all.  

1) Why did Ubuntu default to Lilo this time?
2) Can I change back to Grub?
3) How can I manage my startup services?

---

### Post by ktownhero on 2006-05-12
oh, wait.  I think I might know why it used Lilo.  I'm using XFS this time, maybe Grub doesn't support XFS (or vice-versa)?  

Still, why are there so many things starting up, and how can I manage my bootup sequence?  

Somebody suggested InitNG but I can't figure out how to use it...

---

### Post by Yohumbus on 2006-05-13
Good guess... grub does indeed not support loading the files it needs from XFS (I had this problem on dapper). There is a very simple fix for this though.. what you need to do is create a small (around 30-50mb) boot partition on your hard drive that will be mounted at /boot and will use an ext3 filesystem. I have only done this through the dapper non-graphical install cd so I dont know the easiest way to do this on Breezy but I know it works. If you dont feel like re-installing then all you need to do is use a live cd (I would use Ubuntu live or knoppix) that can run QTParted. then just resize your partion, make a new small one as described and then reboot. Edit /etc/fsab to have an entry mounting your new partion at /boot. then you can reboot or manually mount the partion at /boot and all you need to do then is install the grub package.. Good luck getting your setup to work

---

