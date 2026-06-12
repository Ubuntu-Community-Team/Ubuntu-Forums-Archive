---
title: "Iomega 1 GB Jaz drive"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by urukrama on 2006-08-27
I have an external Iomega Jaz drive (1 GB) that I've used for ages. Since I don't have a CD burner on my laptop, I use it to backup documents. Everything worked fine in Windows (Millenium and later XP), but I haven't been able to use my jaz disks since I moved to Ubuntu.

I installed Jazip through Synaptic, in the hope that would help, but that didn't work entirely. If I run /usr/sbin/jazipconfig as asked to after the installation, the Jaz drive is recognised, and I can then create a mount point, which I did. Nothing shows up at that mount point, however, and the drive never shows up in /etc/fstab (as it should, no?).

If I run Jazip, it recognises the disk and the drive, but for some reason I can't mount the drive. It gives the following error message: "Error trying to mount /dev/sdb : invalid argument".

Does anyone have any suggestions or solutions? I searched the forums but nothing came up. Jaz disks are not that popular ;) 

I am not an expert linux user, but I have been using it for some time and am willing to learn more. I am using Ubuntu Dapper 6.06.1

---

### Post by tageiru on 2006-08-27
> **urukrama said:**
> It gives the following error message: "Error trying to mount /dev/sdb : invalid argument".
You can not mount the device itself, you need to mount a partition on the device, i.e. /dev/sdb1 (there will probably only be one)

---

### Post by urukrama on 2006-10-17
That doesn't work either. Like with /dev/sdb, I get the message that it cannot be found in /etc/fstab or /etc/mtab. Any idea how to add the drive to those?

Hmm... and I can't start jazip either now. Error message:

> 
Can't open device /dev/sdb
Is there a disk in the drive?

---

