---
title: "Triple Boot Ubuntu,WinXp,Xandros"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-05-05
Hello Guys..
this mite be my nth question for today.
But please bear with me.

Presently dual-booting Ubuntu and WinXp
I need to knwo how to install Xandros so that
I now triple boot the system...without corrupting
any of the MBRs.

I nearly installed Xandros..but then just stopped.
I don't want WinXp to get destroyed in the process
as this is the only OS that gives me Internet as of now!!

---

### Post by neouser99 on 2006-05-05
sure, shouldn't be a problem. you'll have to look into how to properly configure grub/lilo, but xandros is just another linux kernel which is easy enough to boot from within grub/lilo.

-neo

---

### Post by ajgreeny on 2006-05-05
No problem hellemt.  I have WinXP, (K)ubuntu and Mepis all together on my machine, admittedly on two hard disks, but that won't make any difference as long as you get the partitioning right in the first place.

It is quite likely that the second linux will not see the first when it installs grub, so you may want to make sure you have the entries for Ubuntu from its own grub, that you can then add to the new grub.  Alternatively install the second linux grub to floppy, if you have one, and then you can start the second linux from floppy, or again just edit the /boot/grub/menu.lst by adding the needed entry for the missing linux.

PS  I'll bet you end up using Ubuntu more than the other linux distro.  I haven't yet found another linux with a sensible forum like this one.  Suse forum was hopeless, Mepis is even worse.  Ubuntu is the greatest! Good luck.

---

### Post by hellmet on 2006-05-06
thnx guys...
will go for the install then..

---

