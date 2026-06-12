---
title: "HELP, Error copying files to USB Drive"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Mr. Papageorgio on 2007-06-04
Hey all,

I have a problem; I keep all my music in my /home directory and I want to move them to my external USB drive but when i try to copy them I get a error, not enough permissions.  

The drive is formated in windows, either FAT32 or NTFS.

---

### Post by taurus on 2007-06-04
You need to know for sure whether it's fat32 or ntfs because you need to install ntfs-3g driver before you can write to ntfs filesystem.  You can, however, write to fat32 with default vfat driver.

```
sudo fdisk -l
df -h
```

---

### Post by Inxsible on 2007-06-04
If you havent installed ntfs-3g then,
Go to Applications --> Add / Remove
Search for ntfs and install the NTFS Configuration Tool.

Then after installation:
Go to Applications --> system Tools --> NTFS Configuration Tool. Enable the write access to both internal and external drives.

After doing the above, or if you have done this already

```
sudo chown -R <your username>:<your group> <device path>
```

should give you the permissions necessary

---

### Post by Mr. Papageorgio on 2007-06-04
Thx for all the help guys!

It is in NTFS format so I installed the driver listed above and enables external drives but I still can't copy to that directory.  

What gives?

---

### Post by Inxsible on 2007-06-05
Can you post the output of the following
```
sudo fdisk -l
```
and ```
 gksudo gedit /etc/fstab
```

---

