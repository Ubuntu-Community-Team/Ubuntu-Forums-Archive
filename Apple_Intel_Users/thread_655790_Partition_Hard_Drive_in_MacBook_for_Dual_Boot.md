---
title: "Partition Hard Drive in MacBook for Dual Boot"
date: 2008-01-01
forum: Apple Intel Users
---

### Post by tachuela on 2008-01-01
I just got an Apple MacBook Intel Core 2 Duo, 1 GB RAM, 120 GB HD. My first attempt at dual boot with 7.10 64 bit ended in wiping out my Apple installation using Gparted. Is it that I have to partition the drive from within Apple? How do I partition for dual boot?

---

### Post by opus_az on 2008-01-01
I haven't tried this, but you might look at:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
(Assusmes you have a Santa Rosa chip)

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
(If it's not Santa Rosa)

---

### Post by cyberdork33 on 2008-01-02
> **tachuela said:**
> I just got an Apple MacBook Intel Core 2 Duo, 1 GB RAM, 120 GB HD. My first attempt at dual boot with 7.10 64 bit ended in wiping out my Apple installation using Gparted. Is it that I have to partition the drive from within Apple? How do I partition for dual boot?

Just make two partitions with DiskUtility (on the DVD) before installing OSX. After installing OSX, boot the Ubuntu Live CD, and start the partition editor (gparted). Select the last partition on the list and delete it.

start the installer, and when prompted, choose to install to the free space.

---

### Post by tachuela on 2008-01-02
Thanks a lot. I'll read the links and try your suggestion cyberdork33. I really appreciate it.

---

### Post by tachuela on 2008-01-04
I didn't find any 'back partition' except a very small one that might be used by 
MacOS. May I use Gparted Live CD to resize the MacOS and make a new partition in the back without touching that small partition?

---

### Post by cyberdork33 on 2008-01-04
> **tachuela said:**
> I didn't find any 'back partition' except a very small one that might be used by 
MacOS. May I use Gparted Live CD to resize the MacOS and make a new partition in the back without touching that small partition?
I said 'last'. If there are only 2 partitions (EFI and OSX) then you did not create 2 partitions with Disk Utility initially, before installing.

You can use gparted to shrink your OSX partition (without affecting the EFI partitions in the front of the drive). I would be sure to boot my OSX DVD and run repairs on the volume afterwards just to make sure though. You do not need to create any new partition in the free space. Then after booting the Ubuntu CD, just choose to install to the free space as normal, and the needed partitions will be created by the installer.

---

### Post by tachuela on 2008-01-04
Thank you. I'll get back to work on that.

---

