---
title: "moving swap mount location"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by strikeback03 on 2007-03-01
When creating all my partitions, I forgot about the limit of 4 primary partitions per hard drive.  So now I have XP and swap, root, and home all as primary partitions, and still have 200gb of space to be my file storage for Windows.  I figure the easiest way to make this available is to merge it with the swap partition, create an extended partition with 2 logical partitions on it, and make one swap and the other my windows data.  How do I go about changing the mount of swap to the new location?

---

### Post by taurus on 2007-03-01
You would edit /etc/fstab and change the entry for your swap.

Applications -> Accessories -> Terminal
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

---

### Post by strikeback03 on 2007-03-01
I assume I have to do the repartitioning and editing from the live CD.  do the fstab changed get automatically written to the file on the hard drive, or do they have to be moved there somehow?

---

### Post by taurus on 2007-03-01
Just mount the root partition, /, from the LiveCD and edit /etc/fstab on your harddrive directly.

---

### Post by strikeback03 on 2007-03-01
well after repartitioning and editing Ubuntu still boots, so I guess I didn't really break anything.  Is there somewhere to check to be sure it is tracking the new swap location?

And should I post other problems in this thread, or nnew threads with new titles?

---

### Post by nyinge on 2007-03-01
What are the output of the following commands?
```
  sudo fdisk -l  
```
and
```
  free  
```

---

### Post by strikeback03 on 2007-03-01
> **nyinge said:**
> What are the output of the following commands?
```
  sudo fdisk -l  
```
and
```
  free  
```

for the fdisk:

```
  Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2           13539       38913   203824687+   5  Extended
/dev/sda3            6896        8560    13374112+  83  Linux
/dev/sda4            8561       13538    39985785   83  Linux
/dev/sda5           14046       38913   199752084    7  HPFS/NTFS
/dev/sda6           13539       14045     4072414+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

```

and for free:
```
              total       used       free     shared    buffers     cached
Mem:       2074892     342576    1732316          0       9096     200072
-/+ buffers/cache:     133408    1941484
Swap:            0          0          0

```

I'm gonna guess swap didn't work then.

---

### Post by taurus on 2007-03-02
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to it.

```
/dev/sda6   none   swap   sw   0   0
```
Save it and mount it.

```
sudo mount -a
free
```
So you see it from the output of the last command?

---

### Post by strikeback03 on 2007-03-02
free still shows:
```
 total       used       free     shared    buffers     cached
Mem:       2074892     545632    1529260          0      17052     335868
-/+ buffers/cache:     192712    1882180
Swap:            0          0          0

```

here's my fstab, if it helps:
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cfdaed96-f835-4df7-b9ae-5cbcbf432bd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=b5cd1dd6-738d-47d8-bf80-0fee9604dee4 /home           ext3    defaults        0       2
# /dev/sda6
UUID=513b7b4c-53f9-45c4-baf7-95933ac9c317 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda6   none   swap   sw   0   0

```

thanks for the help so far, I'm going to bed now, I'll be back tomorrow after work.

---

### Post by taurus on 2007-03-02
Wait, you already have an entry for swap in /etc/fstab!  Therefore, edit /etc/fstab again and remove this line from it.

```
UUID=513b7b4c-53f9-45c4-baf7-95933ac9c317 none            swap    sw              0       0
```
Reboot and see if your swap partition is mounted.

```
free
```

---

### Post by strikeback03 on 2007-03-02
OK, that worked, free shows the swap space now.  Thanks everyone.

Should I start new threads for myo other questions?  Or just post here?

---

### Post by nyinge on 2007-03-02
Great.  

New threads for new questions would be appropriate.  Usually, one question per thread, unless, of course, they're quite related.  :)

---

### Post by indytim on 2007-03-03
Followup question on this thread as I'm faced with the same situation on 2 hd's (duh..):

After removing the /swap and creating additional partitions to drive the extended partition, I assume you will have to modify fstab to reflect the new partition id's after the extended partition has been created.  

Correct?

IndyTim

---

### Post by nyinge on 2007-03-04
Yes, I think you will need to tell the fstab to recognize your new swap partition.  I doubt that it will do automatically.  I've never tried it myself, though.

---

