---
title: "What HD Format For Install?"
date: 2007-03-30
forum: Apple Intel Users
---

### Post by Wee_Guy on 2007-03-30
I tried to install Ubuntu from the Live CD on to my external hard drive, i use it mainly for backing up Mac OS X, but i had room for a partition for Ubuntu. So i put a 10GB (i don't plan on using loads of space on music of videos etc) partition on it which i formated UNIX Filesytem (Linux is UNIX isn't it:confused:)

I ran the installer, but when i got to the partition chooser, it said something about that partition being invalid, or not useable.

---

### Post by david_edmundson on 2007-03-30
There are several different UNIX filesystems, HFS+ is what OS X uses, Linux uses primarily "Ext3". 

If you partitioned it in OS X it probably chose HFS for you. Part of OS X being "user friendly" means not telling you information that's important and useful to a user to drive you crazy and make you stop using it.

In short, when you get to the partition chooser, reformat that partition into Ext3.

---

### Post by Wee_Guy on 2007-03-31
I ran the installer but when i got to the partition chooser (and selected the "reformat drive" option) it said that  there was no root volume. I had set the partition that i wanted for Ubuntu to go on to as the root. Is root '/ ' or is it something else, because i had set '/ ' as the partition for Linux to be installed on.

The partition was a 10GB partition, so i doubt that it could be too small, and i also definately chose the right one, not another one, as that was the only 10GB partition on that drive.

---

### Post by ronocdh on 2007-03-31
Don't use the partition chooser in the GUI installer; you want "Manually edit partition table" option, which'll allow you to reformat, create, even delete partitions. Once there, select the 10G party you sculpted in OS X, and format it, as was said above, in ext3.

(Make sure to click "Commit to changes" in order to actually reformat it.)

From there, you might get a further error about a lack of a swap partition; you can repartition your 10G into 8G and 2G, for example, or you can just wait till after the installation and create your own swapfile.

---

