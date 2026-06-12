---
title: "Need Help Mounting Drives"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by imjosh on 2007-03-10
I just installed Edgy last week and I have spent the past week working through a large portion of my issues.  I am stuck on one final issue, mounting my root, something I thought it did automatically, and mounting my extended partition.  I have been able to mount my windows partition using ntfs-3g.

I have tried searching but I am new to Ubuntu and I am having trouble finding the correct solution in these forums or using Google.:confused: 

My info

sudo fdisk -l

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7837    62950671    7  HPFS/NTFS
/dev/hda2            7838        9648    14546857+  83  Linux
/dev/hda3            9649        9729      650632+   5  Extended
/dev/hda5            9649        9729      650601   82  Linux swap / Solaris
josh@josh-laptop:~$ 


```

fstab info

```
proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=8166dae1-eabb-4f65-acd2-c23e236da74d / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=bd0e82aa-75c3-463f-9b98-317068bb1b4c none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/maindrive ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

If I need to provide any other info let me know and I'll get right on it.

I want to be able to mount these two assuming I understand this correctly.
```
/dev/hda2            7838        9648    14546857+  83  Linux
/dev/hda3            9649        9729      650632+   5  Extended
```

Thanks for any help.

---

### Post by gradedcheese on 2007-03-10
:confused: from what you posted (namely, fstab) it clearly shows that / is mounted...  in fact it has to be, what else would your file system consist of?  That is:

```

ls /

```

is the contents of /dev/hda2...

---

### Post by imjosh on 2007-03-10
Hmm I must be confused then,

I don't understand the error at the end bolded below
```
# Entry for /dev/hda2 :
UUID=8166dae1-eabb-4f65-acd2-c23e236da74d / ext3 defaults,**errors=remount-ro 0 1**
```

---

### Post by taurus on 2007-03-10
It means in case there is an error to your root partition,/, remount it as read-only so you can fix it with fsck.

---

### Post by imjosh on 2007-03-10
> **taurus said:**
> It means in case there is an error to your root partition,/, remount it as read-only so you can fix it with fsck.

Thanks,  to mount the hda3 which is extended format I am trying to determine how I add it to the fstab.

I am confused about the type to specify since it is extended. 

I already made a directory and I want to add to fstab below is as close as I can get using various 

/dev/hda3 /media/linuxstore ext3 defaults 0 0

I am not sure what to use instead of ext3?

I apologize if this has already been covered elsewhere, in retrospect I probably didn't need this partition since I can read/write NTFS, unfortunately i am also unsure of how to merge this partition with my main linux partition.

---

### Post by taurus on 2007-03-10
You cannot mount extended partition.  The space that the extended partition takes up is used by the logical partition under it.  

Look at these two lines.

```

/dev/hda3            9649        9729      650632+   5  Extended
/dev/hda5            9649        9729      650601   82  Linux swap / Solaris

```
Do you see something interesting?  They both start with the same value and end with the same value.

So, you can only mount primary partitions and logical partitions.

[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

---

