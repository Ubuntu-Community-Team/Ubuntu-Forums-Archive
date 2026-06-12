---
title: "Mac Pro booting misery!"
date: 2010-06-08
forum: Apple Hardware Users
---

### Post by Gomff on 2010-06-08
Hi all, first post on here so go easy on me!

I'm trying to install Ubuntu Lucid on my 2008 8 core Mac Pro. I'm going with the 64 bit version since I have 8 GB RAM and intend to put Blender through it's paces.

My system has 4 Hard drives in it. Bay one has a backup of OS X and my intended Ubuntu partition on. Bay 2 is just data. Bay 3 has my working version of OS X and Windows 7 on and Bay 4 is more data. I have installed rEFIt.

I've installed Ubuntu onto my intended partition in Bay 1 but I don't think GRUB is working properly because if all drives are connected to the system, when I select my Linux partition in rEFIt, I get a brief flashing cursor and then the system boots to Windows 7. If I disconnect all the other drives except for the one in Bay 1, I get a flashing cursor for about 15-20 seconds and then finally GRUB appears and gives me the option to boot to Ubuntu. 

When Ubuntu does load, I've managed to get everything working except for the system only shows 2GB of RAM rather than the 8GB that's actually in there.

I've been through the Mac installation Wiki's and searched until my eyes bled, but I can't seem to find how to get my system booting the way I want. I think it's to do with the fact that Ubuntu is on a different partition to my main OS X and Windows 7 disk.....Unfortunately I don't have enough space on that disk to triple boot as I have done on my Macbook pro which works flawlessly.

I'd really appreciate any advice on how to get my system working properly and some guidance on where the right partition is to install GRUB from the advanced tab at the end of the installation options in the Ubuntu setup. On my Macbook Pro install, GRUB appears much more quickly after selecting Linux from the rEFIt menu which makes me suspect it's not working properly on the Mac Pro, and may be contributing to my problems.

Thanks in advance, sorry for the long post.

---

### Post by linuxopjemac on 2010-06-09
[http://refit.sourceforge.net/help/multiple_disks.html](http://refit.sourceforge.net/help/multiple_disks.html)

---

### Post by Gomff on 2010-06-09
Thanks for posting that link.....It explains a lot.

Damn.....What to do now I wonder?

---

### Post by linuxopjemac on 2010-06-09
Boot with grub-efi on one hard disk having the Linux on it, which will hopefully be seen by your Mac when pressing option. I have no experience in that though.

[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

---

### Post by linuxopjemac on 2010-06-09
[http://ubuntuforums.org/showthread.php?t=995704&highlight=efi](http://ubuntuforums.org/showthread.php?t=995704&highlight=efi)

---

### Post by Gomff on 2010-06-09
Thanks for the link but that thread is very long and it looks like a complicated issue that still doesn't have a proper solution. 

Think I might give up on it for the moment :-(

---

