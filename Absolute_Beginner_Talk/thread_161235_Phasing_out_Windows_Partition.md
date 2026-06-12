---
title: "Phasing out Windows Partition"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by sinfreealex on 2006-04-16
My setup:

40Gb (Linux dedicated drive)
    1.44 GiB Swap
    36.85 GiB Ext3

152.66 (Windows drive)
    152.66 NTFS

I would like shrink the NTFS partition down to 40Gb and move it to the end of the drive.  Then, I would like to format the rest of the drive and be able to use LVM to extend my 40Gb to it.  I don't know where to begin.  My Maxblast software is useless (big surprize).  Thanks in advance.

---

### Post by sYs^ on 2006-04-16
I recommend gparted, I did a lots of similar task with that and it worked. :>
or if you want to operate on Windows try Partition Magic

sudo apt-get install gparted
sudo gparted

---

### Post by Qrk on 2006-04-16
[QUOTE=sinfreealex]

I would like shrink the NTFS partition down to 40Gb and move it to the end of the drive.  Then, I would like to format the rest of the drive and be able to use LVM to extend my 40Gb to it. [/QUOTE]

Don't move it to the end of the drive. One of windows quirks is that it doesn't like to be anything other than the first partition.

---

