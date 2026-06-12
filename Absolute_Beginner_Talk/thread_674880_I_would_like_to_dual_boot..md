---
title: "I would like to dual boot."
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-01-22
Now that I have been using Ubuntu for a few months I know that I don't want to go back, but I do have to admit that there are one or two things that I need to be able to do that I can only do in Windows right now. I have a legit copy of Windows, how do I set things up so that I can dual boot without having to completely uninstall linux?

---

### Post by billgoldberg on 2008-01-22
If you only need it for one program (or 2) it would be easier and faster to run windows in virtualbox of vmware.

---

### Post by boriquajake on 2008-01-22
You are absolutely right but I have been unable to get either of those two options to work, nor does WINE do what I need. At this point dual-booting is my only choice for now.

---

### Post by Born-Thirsty on 2008-01-22
I am not sure if you could try use GParted to shrink the linux partition (if you have used the whole harddisk to install linux). Then simply boot from the Windows CD and create a partition for it to load to on the free space. Once installed, I am assuming that you would have to edit the Grub Loader and add the boot command for Windows... hope this helps.

---

### Post by gn2 on 2008-01-22
Are you trying to add Windows to a single boot Ubuntu installation?

If you are, use a [Gparted Live CD]("http://gparted-livecd.tuxfamily.org/") to create some free space by shrinking a partition to leave unallocated space. 

Next boot with the Xp CD and install into the unallocated space, the Windows installer will allow you to create a C: partition.

The installation of Windows will over-write Grub, so you'll have to re-install it, this can be done with an Ubuntu Live CD: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Lots of booting info on the Hermanzone link in my sig, which is an invaluable guide.

---

### Post by billgoldberg on 2008-01-22
Yes, like others said, resize with gparted and then installing xp on the right partition is how this should be done.

But to repair the grub bootloader I suggest the SuperGrubDisk. Everyone dualbooting should have a copy of this awsome live cd. 

[http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

---

### Post by boriquajake on 2008-01-22
Thanks for the tip. That tool looks great.:)

---

### Post by huge3783 on 2008-01-22
I agree use gparted to resize your partion and install xp on the second part. I just did this and was able to reinstall grub from the live CD no problem. However, as of right now I can't boot xp from grub and I am not sure why it doesn't show up on my grub. let me know if you have the same problem.

---

