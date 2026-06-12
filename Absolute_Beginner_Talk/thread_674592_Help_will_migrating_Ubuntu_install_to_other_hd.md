---
title: "Help will migrating Ubuntu install to other hd"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Dunover on 2008-01-21
Hi all

I have been testing ubuntu 7:10 and am very happy with it!
I installed it on a small hard drive but have made some room on my main hard drive and want to install over there.. BUT I would surely like to move he current install and keep as many of the things I have set up. Some programs and stuff would be nice... or at least as much as possible!

Can someone point me in the direction of some easy to understand instructions, on how to migrate over..

Thanks for supporting such a nice product!

Cori

---

### Post by legend2440 on 2008-01-21
This might help

[http://ubuntuforums.org/showthread.php?t=193943](http://ubuntuforums.org/showthread.php?t=193943)

---

### Post by Dunover on 2008-01-22
Thanks, but looks to scary with all that code... is there a way to move things in a graphical format with out getting into code?

Thanks!
Cori

---

### Post by logos34 on 2008-01-22
> **Dunover said:**
> Thanks, but looks to scary with all that code... is there a way to move things in a graphical format with out getting into code?

In that case, I think you're limited to using Gparted:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
(--> section 'Copying a partition')

But you'll have to edit menu.lst and fstab, and reinstall grub.

---

### Post by bodhi.zazen on 2008-01-22
You do not need to re-install grub, but you do have to manually edit a few config files (/etc/fstab and /boot/grub/menu.lst)

Here is a how-to : [http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

---

### Post by logos34 on 2008-01-22
> **bodhi.zazen said:**
> You do not need to re-install grub...

Then how will he boot? Depending on which drive Dunover makes the Bios boot disk, grub either has to be installed to the mbr of the main drive, or reinstalled on the mbr of the small drive so that it points instead to the menu.lst in the new root partition.  Right?

---

### Post by smwny on 2008-01-22
I think gparted will move a partition.

---

### Post by bodhi.zazen on 2008-01-22
> **logos34 said:**
> Then how will he boot? Depending on which drive Dunover makes the Bios boot disk, grub either has to be installed to the mbr of the main drive, or reinstalled on the mbr of the small drive so that it points instead to the menu.lst in the new root partition.  Right?

Oops, missed that, I guess I assumed he would set the new drive as master, but then now that you mention it he would need to copy the MBR from the first drive or re-install grub ...

I use a /boot partition and chainload all my OS ...

---

### Post by Dunover on 2008-01-22
I have the "temp" version of ubunto on the slave....so will be moving or reinstalling on the master drive.

If I do a back up in the backup program would I just do a "restore".   What would that restore? Programs or just settings?
I don't mind reinstalling programs... as I would think it would be better maybe?  But my setting esp thunderbird would be nice to move

Corisa

---

