---
title: "fsck startup errors"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-08-12
I had a problem with my Ubuntu install and had to do a weird data migration thing that meant i had to resize HDA3 at the right hand edge of the drive to take up the whole drive. Now FSCK is giving me errors when i boot up into Ubuntu Feisty. The only other partition on my drive is a 1.5gb Swap Partition.

My fsck error log is

```
Log of fsck -C -R -A -a 
Sun Aug 12 12:24:25 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=96ed5be7-c476-49d5-b0cf-e1119e775f25'

fsck died with exit status 8

Sun Aug 12 12:24:25 2007
----------------
```

After i get the error message, it tyells me to srot the problem manually then puts me into a recovery shell as root. After typing reboot in the recovery shell though GDM starts up and everything runs perfectly.

Im guessing that some of the data is corrupted and it will be easy enough to fix by a reinstall. Other than that im guessing its a hard drive internal error. Which is bad.

---

### Post by happyhamster on 2007-08-12
You could try checking if the UUID's in fstab are still correct.

1. This command lists your partitions (/dev/sda1, /dev/sda2, etc):

sudo fdisk -l

2. Determine the correct UUID for a partition:

sudo  /sbin/vol_id   -u   /dev/....

(where /dev/.... 's a partition name found in step 1)

3. Backup fstab:

sudo cp /etc/fstab /etc/fstab.original

4. Edit fstab to use the correct UUID(s):

gksudo gedit /etc/fstab

---

### Post by 1/0 on 2007-08-12
Maybe this might be of help? [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

What's in your fstab?

---

