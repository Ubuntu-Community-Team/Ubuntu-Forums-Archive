---
title: "Problems with Linux network (nfs)"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by tico on 2007-08-13
I've got 2 problems with my network (nfs):

1. the folders don't automount when I restart the system, evem if I have put the following line in my /etc/fstab
[hostsIP number]:/home	/mnt/Toshiba/home	nfs	rw	0	0

2. In computer 1 I have shared  3 NTFS partitions that are mounted in /media/sda1, /media/sda2, /media/sda3. But when I tried to mount them in computer 2 I get a "permission denied" error message.

Could you please help me with these 2 problems?

Thanks.

---

### Post by be4truth on 2007-08-13
Did you install portmap?

```
sudo apt-get install portmap
```
This is needed to connect two machines.

---

### Post by tico on 2007-08-13
Yes, portmap is installed.

Another problem: I can manually mount my /home directory, but I can't get access to some of its subdirectories (e.g. Desktop). Why can I access some subdirs and not others?
 Thanks.

---

