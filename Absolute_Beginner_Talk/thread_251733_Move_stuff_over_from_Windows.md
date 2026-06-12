---
title: "Move stuff over from Windows"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by MiThRaZoR on 2006-09-05
How can I access the partition Windows is on. I could get to it but it says, "Unable to mount selected volume."

I'm trying to move my whole music collections onto the Ubuntu partition.

---

### Post by aysiu on 2006-09-05
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help.

---

### Post by MiThRaZoR on 2006-09-05
> kudafi@kudafi-desktop:~$ sudo umount /media/hda1
umount: /media/hda1: not found

I'm sure that's not what it's supposed to say it.

---

### Post by aysiu on 2006-09-05
Well, /media/hda1 was just an example, actually.

When you run the *sudo fdisk -l* command, you should see where you Windows partition is located--it'll be either NTFS or FAT32. On my computer, it's /dev/hda1. Yours might be /dev/hda2 or /dev/hda5 or /dev/hdb1.

---

