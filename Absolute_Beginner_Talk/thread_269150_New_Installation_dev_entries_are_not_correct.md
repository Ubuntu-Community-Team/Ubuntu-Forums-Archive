---
title: "New Installation /dev entries are not correct"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by AlfWickens on 2006-10-01
I have just installed Ubuntu 6.06 on a Pentium IV PC. The installation proceeded without incident. The computer has a CD-ROM drive a floppy drive and an ATAPI(IDE) ZIP 250 drive. I get an error when I try to mount the zip drive in the file browser. The error message is - error : device /dev/hdb4 does not exist. 

The zip drive is installed as the primary slave device. When I look in the /dev folder the device file listings for the floppy drive and the zip drive are - 

brw-rw---- 1 root floppy 3 64 2006-10-01 hdb
brw-rw---- 1 root floppy 3 65 2006-10-01 hdb1

I tried a Kubuntu installation last week and had similar problems, although in that case I believe that the floppy was correctly identified. I switched to UBUNTU so that I am working in the same environment that most of the support documentation refers to.

How are the /dev entries set up at install time?
How do they relate to driver installation or configuration?

I tried using mknod in KUBUNTU and got the floppy to work but was unable to get the zip drive working. I'm not sure exactly what mknod is doing except point to the hardware as defined by the major/minor numbers. What happens if I delete one of the existing entries as shown above?

---

### Post by AlfWickens on 2006-10-05
I have found that the /dev entries are set up correctly if I re-install Ubuntu with a floppy disc in the floppy drive and a zip disc in the zip drive.

I am able to mount and unmount the discs, but the zip disc will not eject!! I have tried the eject command but this doesn't work. Any advice would be appreciated.

---

