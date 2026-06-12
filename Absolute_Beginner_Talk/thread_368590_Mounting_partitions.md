---
title: "Mounting partitions"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-02-23
When I run live CD so I can play around with Ubuntu without installing it on a hard drive I find that I can't access my hard drive partitions.  I have a C: partition, a D: partition, and an E partition.  The E: partition is available from the get-go in Ubuntu.  I think that has something to do with the fact that it is an external USB drive.  The other two partitions, though, are part of a single SATA II 250GB hard drive.  If I run sudo fdisk -l (I think that's right) I can see the C: and D: partitions, but from that point I don't know how to gain access to them.  How do I do this?  They are NTFS partitions, but so is the USB external hard drive, so I'm hoping this won't make a difference.  Could they be not automatically setup in Ubuntu because they are NTFS?  And if so, if I change my D: drive to FAT32 do you think it will be accessible to Ubuntu automatically upon loading Ubuntu via live CD?

---

### Post by rsambuca on 2007-02-23
The drives have to be mounted in order to access them from the live cd.

First make a directory to mount them to.  There is a directory called /mnt already, so it is common to make a subdirectory in that folder```
mkdir /mnt/newdrive
``` where "newdrive" can be whatever you want to call it.

Then mount the desired drive to the directory```
sudo mount /dev/sda1 /mnt/newdrive
```You will have to replace "sda1" with the appropriate drive partition you want to mount.

You should then be able to access the new drive by going to the /mnt/newdrive directory from your Places menu.

---

### Post by taurus on 2007-02-23
Can you post the output of this command here then?

```
sudo fdisk -l
```

---

