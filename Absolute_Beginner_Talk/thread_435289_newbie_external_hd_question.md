---
title: "newbie external hd question"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by moheganer2 on 2007-05-06
I am new to linux and have installed ubuntu 7.04 When using windows i downloaded media files and kept them on an external hard drive.in ubuntu i can access and play these files but cant erase or send newly downloaded media files to the hard drive.Is there a way to do this ?

---

### Post by ubnewbie2 on 2007-05-06
Must be a permissions problem.  Try taking ownership of the files with something like

sudo chown <username> <files>

---

### Post by taurus on 2007-05-06
What filesystem is that external harddrive?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by taurus on 2007-05-06
> **ubnewbie2 said:**
> Must be a permissions problem.  Try taking ownership of the files with something like

sudo chown <username> <files>

The command chown won't work for ntfs/vfat filesystem.

---

### Post by nonewmsgs on 2007-05-06
automatix has an automatic mount and that protocol for reading and writing ntfs.

---

### Post by moheganer2 on 2007-05-06
output from terminal     Disk/dev/s                                                                                                                    db:60.00gb,60060155904bytes                /dev/sdb1 1of 7  system:hpfs/ntfs

---

### Post by taurus on 2007-05-06
Here's a link for you then.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by moheganer2 on 2007-05-06
thanks everyone for your help. the automatix program solved the problem.

---

