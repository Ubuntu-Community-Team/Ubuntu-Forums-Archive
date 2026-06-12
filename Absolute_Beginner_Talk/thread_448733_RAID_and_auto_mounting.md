---
title: "RAID and auto mounting"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by finchy on 2007-05-19
Hi fellas

First of all I want to mount three raid partitions: These are four commands I need to run every time system is started. 

[PHP]
dmraid -ay -v 

mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_jfbfifcj1 /media/c/ 

mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_jfbfifcj5 /media/d/ 

mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_jfbfifcj6 /media/e/ 
[/PHP]

Now, my question is where to put that commands that after system is started all of these partitions are automatically mounted? Many thanks for reply. (Oh, I've tried with etc/init.d , it doesn't work)

---

### Post by overdrank on 2007-05-19
> **finchy said:**
> Hi fellas

First of all I want to mount three raid partitions: These are four commands I need to run every time system is started. 

[PHP]
dmraid -ay -v 

mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_jfbfifcj1 /media/c/ 

mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_jfbfifcj5 /media/d/ 

mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_jfbfifcj6 /media/e/ 
[/PHP]

Now, my question is where to put that commands that after system is started all of these partitions are automatically mounted? Many thanks for reply. (Oh, I've tried with etc/init.d , it doesn't work)

Hi maybe this link will be of some help
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Good luck!:guitar:

---

### Post by igloocentral on 2007-05-24
do you need to run the dmraid command every time? If you have dmraid installed properly, it should automatically activate your raid sets when you boot. when you reinstall it, make sure your /boot is not read-only - i think dmraid updates the initramfs to give it the ability to use /dev/mapper devices when you install it.

then the mount statements will go in your /etc/fstab.

---

