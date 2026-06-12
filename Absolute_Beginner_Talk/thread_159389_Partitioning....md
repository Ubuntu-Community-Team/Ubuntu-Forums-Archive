---
title: "Partitioning..."
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Love&lt;3Duckie on 2006-04-12
Hey there.

I recently got Ubuntu today and was excited to install it.

So I got the image burnt onto CD and I booted up from it (after changing BIOS config. boot from CD) and to wonder whether Ubuntu will overwrite my Windows partition on the hard-drive.

Now I know it may seem easier to get a new hard-drive or get the Live CD, but I want Linux on my PC to use for good.

So is it possible to have Windows & Linux/Ubuntu partitioned on the same hard-drive? If so, how is it done on the installation?

Thanks if you can help.

---

### Post by aktiwers on 2006-04-12
Before I deleted Windows XP, I did this.

If you make sure there is some free space (unpartitioned space) before you start the installation. Then you could just create a SWAP drive and a Root drive manually in the installation and install it normally.

For me it installed GRUB automaticly, which will give you access to pick wich OS to boot when you start up your computer (dual boot).

Hope this helped.

---

### Post by az on 2006-04-12
[QUOTE=Love<3Duckie]Hey there.



So is it possible to have Windows & Linux/Ubuntu partitioned on the same hard-drive? If so, how is it done on the installation?

Thanks if you can help.[/QUOTE]

Yes, by defaul, the installer will detect your other OS and offer to shrink it's partition for you.  Just make sure you pick that option.

If you are not offered that option, you may not have enough free space (2.2 Gig or more) free, or you may need to defragment your windows partitoin first.

It is very very common for people to dual-boot ubuntu and windows like that.

The installer is very safe and reliable, but that is no excuse for not backing up your important data.

---

### Post by catlett on 2006-04-12
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) Follow that link it is a very good guide. Just one bit of advice. If you have software to create a backup, do it. Things can happen however unlikely. If you have a backup you don't have to worry.

---

