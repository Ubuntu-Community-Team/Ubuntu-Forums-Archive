---
title: "External hard drive problems"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by jcorden on 2007-10-19
Two queries

My system is dual boot Ubuntu and Vista. Each OS is on a separate hard drive.

1) I had the system set up so that Ubuntu could read/write to the Vista disk and Vista could read/write to the Ubuntu disk. This worked ok until Vista failed to shut down properly. Next time I booted Ubuntu I lost the link to the Vista drive - how should I fix this.

2) I have just purchased a 500GB Seagate external hard drive (connected via usb). It is appearing as a device on Ubuntu but I can't read or write to it. I have created a mount point called external in mnt and I'm aware that I need to mount it using a command like

sudo mount -t ntfs -o unmask=000 /dev/hdb1 /mnt/external

I don't understand the /dev/hdb1 bit

How do I find out what this disk/device is called.

Should I mount it as ntfs or fat32

---

### Post by Lord_Dicranius on 2007-10-19
1) I've ran into this issue before when my external hard drive (which is formatted in NTFS) didn't unmount properly in Windows (the USB cable was unplugged before it could be "removed safely").  So when it was plugged into my Ubuntu box, it gave me an error saying that a bit wasn't set to show that it was removed safely last time.  I can't remember the exact command (maybe somebody can help me out with that?), but I remember using a "-force" (or something along those lines) in the mount command.  I saved the command in a text file, but it's on my home PC and I'm at work still :(
2) The "dev/hdb1" part is how linux identifies your hard drive (specifically partitions), just like how Windows reads partitions as C:\, D:\, etc.  As for how you should mount it, NTFS or FAT32, it depends on which file system your external hard drive is formatted in, either NTFS or FAT32.  I'm not sure how to check that in Ubuntu, but I know if you plug it into the PC while booted into Vista, you can right-click on the drive and select PROPERTIES, and it should tell you which file system the external hard drive is formatted in.

---

