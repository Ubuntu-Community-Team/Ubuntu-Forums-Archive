---
title: "fschk wont finish on boot!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by HornedBeast on 2007-06-12
Hello...

Ive been using Ubuntu for about a month now and everything has been running really smoothly (including my dual boot into Vista which runs as needed). However, today when i turned on... it said it was going to run a fschk because it had mounted the drive 34 times and hadnt been checked. However.. it gets to about 80% and just stops and will not finish.

Is there anyway to stop this from happening or a fix for the problem? I highly doubt the file system is currupt as all i do is browse the net, nothing special. I can't get into recovery mode or anything! I can pretty much get as far as Grub and choosing an OS. Is there something I can apend to the command line in Grub to get it to not check the disk or do a manual check with a force fix or something? I dont know...

Any help regarding this would be apreciated.

Thanks in advance.

HornedBeast.

---

### Post by Herman on 2007-06-12
Hello HornedBeast

Boot a Live CD and first check your partition numbers with GParted or QTParted, or in a terminal with 'sudo fdisk -lu'.

When you know which partition you want to check, try this,
```
sudo e2fsck -y -f -v /dev/hda2
```That should fix it, and then maybe do this too for good measure,
```
sudo e2fsck -C0 -p -f -v /dev/hda2
```Where: the partition to be checked is /dev/hda2 and it has an ext3 filesystem. Please replace the disc and/or partition number of your installation is different. Or replace the 'hda' part with 'sda' if you have an SCSI or Sata disc instead of IDE.

If it stops please just wait a while as it may be busy fixing something. A reasonable length of time to wait would be five or ten minutes I guess. It would be extremely rare for it to be busy for that long. Normally it would only pause for a few second at the most. 

Regards, Herman :D

---

