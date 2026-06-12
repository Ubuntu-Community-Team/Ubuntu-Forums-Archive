---
title: "[SOLVED] Automatic mount fstab HDD not mounting ?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-11-14
Hi,

I am doing the [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) and when i add the line [COLOR="SeaGreen"]/dev/sdc1    /media/mynewdrive   ext3    defaults     0        2[/COLOR]

i get nothing

my fstab file:
[COLOR="SeaGreen"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f4897cc-2153-4750-9d4c-4324e97ab838 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b3cdf751-58b0-4d22-b19a-df738b7da172 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0[/COLOR]

[COLOR="Red"]/dev/sdc1    /media/mynewdrive   ext3    defaults     0        2[/COLOR]

any ideas what im doing wrong?

---

### Post by Partyboi2 on 2007-11-14
Did you reboot after adding and saving it to fstab?
or try:
```
sudo mount -a
```

---

### Post by hopelessone on 2007-11-14
yep..rebooted...

ubuntu@ubuntu-desktop:~$ sudo mount -a
[sudo] password for ubuntu:
mount: mount point /media/mynewdrive does not exist
ubuntu@ubuntu-desktop:~$ 

hope you can help...

---

### Post by kpkeerthi on 2007-11-14
```

sudo mkdir /media/mynewdrive

```

Create the directory where you want your partition mounted.

---

### Post by hopelessone on 2007-11-14
kpkeerthi - Thanks mate you're the best...!!

---

