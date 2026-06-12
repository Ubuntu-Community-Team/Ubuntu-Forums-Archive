---
title: "[SOLVED] Can't Mount or Format External Volume"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-05-25
I recently formatted my external hard drive to vfat... 

Decided I wanted to use ext3 instead so I just did 

mkfs.ext3 /dev/sdb1

the terminal shows that the process completes fine, however I can not mount the ext3 system and  i get the following message

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or other error


How can I completely erase this drive and start from scratch?

---

### Post by drowner on 2007-05-25
I actually don't know the answer to this, but is i because you can't make a fat32 a ext3 like that, do you have to delete the partition first?

---

### Post by taurus on 2007-05-25
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by kernel tom on 2007-05-25
here's the part for that drive... i know it's sdf on this comp


Disk /dev/sdf: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        7108    57094978+  83  Linux
/dev/sdf2            7109        7296     1510110    5  Extended
/dev/sdf5            7109        7296     1510078+  82  Linux swap / Solaris


it mounts fine now after more work, and seems to be in ext3 format...

what is necessary to format it to fat32 so I can use it on all OS's

---

### Post by taurus on 2007-05-25
You can use gparted, System -> Administration, to reformat it to fat32/vfat.  Make sure you unmount it first before you format it though.

---

### Post by kernel tom on 2007-05-25
worked great!

Thanks!

---

