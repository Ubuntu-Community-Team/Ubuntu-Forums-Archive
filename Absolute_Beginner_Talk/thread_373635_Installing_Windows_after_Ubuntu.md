---
title: "Installing Windows after Ubuntu"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by scumboss on 2007-03-01
Hi Guys

I've installed Ubuntu on my laptop although now I want to install Windows.  Using the Ubuntu live CD I resized the /dev/hda1 partition then created a new partition (/dev/hda3) which is formatted NTFS.  The problem is when I boot using the Windows installation CD it only sees one partition, the whole disk!  It doesn't see the NTFS partition I created using GParted.  There are loads of guides on the net but all of them show you Windows install then Ubuntu.

Help.  :(

Screenshot of partitions: -

[IMG]http://img526.imageshack.us/img526/8886/helpuz9.png[/IMG]

---

### Post by userundefine on 2007-03-01
Yes, you're going to have problems doing this.  It's possible but a pain.  Windows likes to be the only thing on the hard drive and therefore it does not recognize other operating systems running.  And, even if you do get it installed on its own partition, Windows overwrites the MBR and erases Grub leaving your Ubuntu unbootable, and you have to use a LiveCD to write grub back.  It's better to install Windows first, then Ubuntu.

But Windows should nevertheless see an ntfs partition.  Does it at least list that you have partitions on the drive and that it isn't without a partition table?  That's odd if it doesn't.

---

### Post by DirtDawg on 2007-03-01
Oops, disregard this. I misread the O.P. Sorry!

---

### Post by scumboss on 2007-03-01
Thank you for replying Userundefined.  Yes, Windows only sees one partition it recognises as an NTFS partition but the size is the total size of the disk.  I guess I could install Windows then use this guide am I correct?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Although, maybe it's best just to start again and install Windows first.  Stupid Windows. :mad:

---

### Post by userundefine on 2007-03-01
Yes, you would use that guide.  But, I don't know how customized your install is at this point, but I'd save any important files you've made and just install Windows and then reinstall Ubuntu.  It's really so much less of a headache, particularly since Windows partitioner doesn't seem to properly recognize the partition table on your hard drive for whatever reason.

---

### Post by scumboss on 2007-03-01
I took your advice.  I'm now installing Windows. :)

---

