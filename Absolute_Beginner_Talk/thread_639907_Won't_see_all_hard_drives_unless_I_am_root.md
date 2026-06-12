---
title: "Won't see all hard drives unless I am root"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by andhar on 2007-12-13
I loaded up my file server (new install of 7.10) it works flawlessly cept for one minor detail...

 I have 6 hard drives in it, when it boots to desktop as a normal user it auto mounts 1 drive to get the rest mounted I have to SU and double click on the drives in nautilus. 

Is this an ownership issue cuz they do auto mount when I click on them (It askes for the root password).  under permissions it says owner root. 

How do I changed this!? please help!

---

### Post by taurus on 2007-12-13
Did you have all the entries in /etc/fstab to mount them?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by andhar on 2007-12-13
andre@selene:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ad859ce5-585c-4285-8699-f8369d704276 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=3630626E30623551 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=d873bd65-fa5f-4753-9acf-fe03baeca2e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

andre@selene:~$ su
Password: 
root@selene:/home/andre# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ad859ce5-585c-4285-8699-f8369d704276 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=3630626E30623551 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=d873bd65-fa5f-4753-9acf-fe03baeca2e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
root@selene:/


This is the output i got.

I've tried what this thread says but it wont let me rename or change the permissions 
[IMG]http://i26.photobucket.com/albums/c150/andhar/Screenshot.png[/IMG]
[IMG]http://i26.photobucket.com/albums/c150/andhar/Screenshot-1.png[/IMG]

[http://ubuntuforums.org/showthread.php?t=389479](http://ubuntuforums.org/showthread.php?t=389479)

---

### Post by andhar on 2007-12-14
ttt

---

### Post by taurus on 2007-12-14
Since it's ntfs filesystem, why not use ntfs-3g to mount it so you can write to it without worrying changing ownership or permission.

Edit /etc/fstab

```
sudo nano -Bw /etc/fstab
```
and replace this line

```

UUID=3630626E30623551 /media/sda2 ntfs defaults,umask=007,gid=46 0 1

```
with this new line.

```

UUID=3630626E30623551   /media/sda2   ntfs-3g   defaults   0   0

```
Save it with <Ctrl>o and exit with <Ctrl>x.  Then, install ntfs-3g driver with

```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Reboot and see if you can write to /media/sda1 now.

---

