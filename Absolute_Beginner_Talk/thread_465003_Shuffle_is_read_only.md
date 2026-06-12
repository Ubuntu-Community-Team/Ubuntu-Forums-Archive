---
title: "Shuffle is read only"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by jerryz on 2007-06-05
My shuffle mounts as read only. I tried to change but get back an error that it's a read only device?

---

### Post by MagisterJoe on 2007-06-05
Can you please run the following two commands in a terminal and post their output?

```
lsusb
cat /etc/fstab
```

---

### Post by jerryz on 2007-06-05
The output to the commands is. And thanks in advance

Bus 005 Device 005: ID 05ac:1301 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000  
jz@jz-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e5bf864c-fa3f-43e6-b3a2-36463ec466d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=eda0ade6-2a56-4c8d-86be-4566bccfb6d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Inxsible on 2007-06-05
have you tried changing permissions?

```
sudo chown <your username>:<your group> <device mount path>
```

---

