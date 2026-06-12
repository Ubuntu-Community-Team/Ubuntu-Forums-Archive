---
title: "Delete Partition Using QTParted"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Derspankster on 2007-01-24
I recently added a second hard drive to my Edgy system because I wanted to rip all my CD's and serve music from my Ubuntu computer. The new hard drive is 160 GB. I used QTParted to format the new drive and then I partitioned it into 2 partitions, both ext3.  I would now like to just delete one of the partitions and use it as one 160 GB drive.  I don't know how to do this and I get an error when I run sudo qtparted. 

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
Error: File system has an incompatible feature enabled.

I have no idea what that error means and I'm afraid to go any further. QTParted does start and I can see both drives and both partitions of drive 2.  I'm used to using Partition Magic in Windows where you can delete and merge partitions.  

I also don't know how to mount the drive so I can add folders to it. I was able to mount the first partition of the new drive as Music and write my mp3's. I guess I'm just confused and am not sure I've adequately described my issue. Hopefully someone can sort through my ramblings and get me straightened out.

---

