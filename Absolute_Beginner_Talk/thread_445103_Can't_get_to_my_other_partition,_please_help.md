---
title: "Can't get to my other partition, please help"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-05-15
I installed Ubuntu 7.04, and I cannot edit files on my other partition.   When I look at the properties, it says the owner is root, and since I'm not the owner I can't do anything. I set myself as a member of root, but still no luck.  Can anyone help me with this?

---

### Post by taurus on 2007-05-15
What is the filesystem of the other partition?  If it is ntfs, then you need to install ntfs-3g before you can write to it.  Also, how do you mount that other partition, by hand or from /etc/fstab?

```
cat /etc/fstab
sudo fdisk -l
```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Jhorra on 2007-05-15
They were mounted when it installed, this particular drive is a USB external.  I thought it installed with the ability to read/write ntfs.  Are there directions for how to do this?  I found some before, but they didn't work for me.

---

### Post by Happy_Man on 2007-05-15
```
sudo apt-get install ntfs-3g ntfs-config
``` gives you write access. 

Also, run ```
gksudo nautilus
``` and then go and change the owner of the drive to you.

---

### Post by taurus on 2007-05-15
Open a terminal and install ntfs-3g with

```
sudo aptitude update
sudo aptitude install ntfs-3g ntfs-config
```
Then, unmount your external harddrive first and run

```
gksudo ntfs-config
```
to mount it again with ntfs-3g driver.

Otherwise, post the output of this command here.

```
sudo fdisk -l
```

---

### Post by Jhorra on 2007-05-15
Wow, that was a lot easier than the 20 steps I found to do it before.

---

### Post by Jhorra on 2007-05-15
When I run nautilus, I don't see the other partitions, only the file system.  Do I need to mount them in nautilus before I can change the permissions?

---

### Post by Jhorra on 2007-05-15
That did it, thank you guys a lot.

---

