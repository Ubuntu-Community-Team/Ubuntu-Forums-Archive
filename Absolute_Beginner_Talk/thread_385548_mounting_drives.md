---
title: "mounting drives"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by lahook on 2007-03-15
i installed a extra hard drive to my system and formatted it with gparted to ext3.
i've been trying to mount it but not having any luck.

i edited /etc/fstab and added:
/dev/hdb1 /extra  ext3  defaults,-rw   0  0

then tried 
sudo mount /dev/hdb1
no luck
sudo mount /dev/hdb1 /extra
no luck

what am i doing wrong?
where's some docs on mounting drives?
i want to be able to read and write to the drive like it's my home directory.
any help will be appreciated

---

### Post by rusty4r on 2007-03-15
Try this link
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

The beginning describes partitioning, you can just skip down to the part where it describes mounting "/storage" 

Hope that helps

---

### Post by lahook on 2007-03-15
thanks that helped
i just expected it to show up as a drive not a folder

---

