---
title: "Completely NEW to Linux"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by snakestud on 2006-08-20
Can someone help me?  I would like to try out the Linux software but I am having trouble with the "[COLOR="Red"]Live[/COLOR]" cd.  When I boot my computer, it just proceeds to the current OS that I have, Windows XP.  How do I properly install this cd so my computer will open with the Linux OS?  Help please.](*,)

---

### Post by gerbman on 2006-08-20
> **snakestud said:**
> Can someone help me?  I would like to try out the Linux software but I am having trouble with the "[COLOR="Red"]Live[/COLOR]" cd.  When I boot my computer, it just proceeds to the current OS that I have, Windows XP.  I do I properly install this cd so my computer will open with the Linux OS?  Help please.](*,)You need to configure your BIOS to boot to the CDROM first. This isn't hard, you should see a "boot options" or "setup" choice when you first turn on your computer.

---

### Post by win_zik on 2006-08-20
Also make sure that you burned Ubuntu as an iso image as described here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Hope this helps. :D

---

### Post by stormblue on 2006-08-20
You probably have to hit F2 or delete on start up.  Where you see it checking for RAM and displays your harddisk.  If you don't see this then you should see a OEM screen (HP, DELL, Gateway, etc, etc). You can press it then.

What brand is your computer?

Once you enter the bios you're looking for something labeled "boot" or "boot order" change this so CD-ROM is above the harddrive in the list.

---

### Post by wagerrard on 2006-08-20
Just to be clear about how this works, once you set the boot order to look first at the CD drive, you do not need to reset it to boot Windows. The BIOS will roll over to select the hard drive if there's nothing bootable in the CD drive.

---

### Post by otherMark on 2006-08-20
When you switch on the puter there is a mini OS that starts up called "BIOS". It looks for your main OS (windows/linux/whatever) on your floppy, CD or hard drives in a certain order. You can change that order by editing the bios. Hitting the delete button usually gets you there after switching on power(it might be f8 or something else though). You can then find "boot sequence" in the advanced menu. You want 1)floppy, 2) CD, 3) HD1 (or whatever it calls the hard drive).

---

