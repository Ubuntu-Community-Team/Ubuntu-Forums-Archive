---
title: "A few questions...  mounting/ntfs"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by spookyct on 2008-01-25
Hey guys..

I have a few questions...  I just created partitions of size 50GB (ntfs) and 64GB(ext3) with gparted.  How can I see/write to those partitions inside ubuntu?

Second...  I am planning on installing Win XP through vmware.  Any ideas on if should I write this to the ntfs partition or not?

---

### Post by Bachstelze on 2008-01-25
For ext3 : [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

For NTFS : [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

For vmware, it is a bad idea to let it access a physical partiton if you don't know what you're doing. Instead, just create a virtual drive, which can pe sored anywhere, regardless of the filesystem.

---

### Post by spookyct on 2008-01-25
thanks for the reply...  I forgot to mention that this is all on one disk...  including my ubuntu partition.  Where should i start for the mounting process?

---

### Post by Bachstelze on 2008-01-25
Point 5 (create a mountpoint).

---

### Post by spookyct on 2008-01-25
```


james@james-desktop:~$   sudo mkdir /media/ntfs
[sudo] password for james:
james@james-desktop:~$ sudo mount /dev/sda3 /media/ntfs
mount: special device /dev/sda3 does not exist

```

the partitions are located at /dev/sda3 and /dev/sda4 according to gparted.

---

### Post by Bachstelze on 2008-01-25
Sure of that ? Do a

```
sudo fdisk -l
```

and paste the output.

---

### Post by seventhc on 2008-01-25
You can go into Add/Remove and search for ntfs there is a tool that will allow you to read/write to ntfs. If it doesnt show in your search look in the top right corner and change it to all available software.
With this tool it will mount automatically for you.

---

### Post by spookyct on 2008-01-25
yea..  that was it...  i was on sdb3 and sdb4

looks like it worked..  thanks!

---

