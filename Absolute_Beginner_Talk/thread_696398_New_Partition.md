---
title: "New Partition"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by th1bill on 2008-02-14
I have a 36gb new partition on my harddrive and my Ubuntu is on the same drive with a 5.66gb partiton.  Through the use of gparted I have managed to format this partition to ext3 but how do I mount it to be used?

---

### Post by oedha on 2008-02-14
when you login to your desktop....i think it will mounted automatically......
if not you have to mount it manually.....
sudo fdisk -l will help

---

### Post by th1bill on 2008-02-14
I believe I need to mount the hda2 partition by hand but do not know how.  Fdisk -l shows that it is there and gparted shows that it is formated bur it did not mount on the reboot.

---

### Post by emarkd on 2008-02-14
Here's a good guide:  [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by th1bill on 2008-02-14
> **emarkd said:**
> Here's a good guide:  [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I went there and when i <sudo cp /etc/fstab /etc/fstab_backup> i receive <cp: cannot stat '/etc/fstab': No such file or directory.

When I went into the file system fstab is just not there.  I downloaded a new copy of Ubuntu 7.10 a week or so ago and the install disk was burned from that image.

---

