---
title: "flashdrive well not delete in ubuntu"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by wayway1981 on 2008-02-26
how do you format a flash drive in ubuntu the file says it is a read only so i went into and try to change it too "change and delete" but the system say it well not let me tryed delete but said "read only" can not place in trash:confused:

---

### Post by taurus on 2008-02-26
What filesystem is your USB drive and how did you mount it?  Open a terminal and post the outputs of these commands here.

```
sudo fdisk -l
mount
```

---

### Post by wayway1981 on 2008-02-26
pc@pc-desktop:~$ sudo fdisk -l
[sudo] password for pc:

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000459a4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        2434      859477+   5  Extended
/dev/hda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sda: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         984     7897056    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 12)
pc@pc-desktop:~$

---

### Post by wayway1981 on 2008-02-26
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         984     7897056    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 12)
pc@pc-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
/dev/sda1 on /media/WAYWAYS type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

---

### Post by taurus on 2008-02-26
Try

```
sudo umount /dev/sda1
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
ls -la /media/sda1
```

---

### Post by wayway1981 on 2008-02-26
pc@pc-desktop:~$ sudo umount /dev/sda1
[sudo] password for pc:
pc@pc-desktop:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
pc@pc-desktop:~$ sudo mkdir /media/sda1
pc@pc-desktop:~$ sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
pc@pc-desktop:~$ ls -la /media/sda1
total 4528
drwxrwxrwx   7 root root    8192 1969-12-31 19:00 .
drwxr-xr-x   5 root root    4096 2008-02-26 21:54 ..
-rwxrwxrwx   1 root root   23741 2008-02-04 19:18 2007_Federal_1040.pdf
drwxrwxrwx   2 root root   12288 2008-02-07 06:22 dvds
-rwxrwxrwx   1 root root 4033360 2008-02-24 03:33 flyer.pdf
drwxrwxrwx 117 root root    8192 2008-02-15 22:50 jams
drwxrwxrwx   2 root root   20480 2008-02-07 06:39 links
drwxrwxrwx  42 root root  106496 2008-02-15 22:51 ODDS AND ENDS
-rwxrwxrwx   1 root root  394217 2008-02-24 05:40 SPRINGFIELD_Book_armory_PW9108LP.pdf
-rwxrwxrwx   1 root root    1555 2008-02-24 07:23 THE ONLY PLAN I CAN DO.doc
-rwxrwxrwx   1 root root    1120 2008-02-24 00:38 THE PLAN.doc
-rwxrwxrwx   1 root root    1148 2008-02-24 00:45 USA PLAN.doc
drwxrwxrwx   3 root root    8192 2008-02-26 08:11 WORD FILES
pc@pc-desktop:~$

---

### Post by taurus on 2008-02-26
Now, you can write or delete stuff on your USB drive.

---

### Post by wayway1981 on 2008-02-26
[[IMG]http://img525.imageshack.us/img525/5594/screenshotnautiluscw6.png[/IMG]](http://imageshack.us)
[[IMG]http://img525.imageshack.us/img525/5594/screenshotnautiluscw6.5c3c2f8184.jpg[/IMG]](http://g.imageshack.us/g.php?h=525&i=screenshotnautiluscw6.png)

still well not let me delete it????

---

### Post by taurus on 2008-02-26
Are you trying to change permissions or are you trying to delete a file?

What happens when you run this command from a terminal?

```
touch /media/sda1/testing
```

---

### Post by wayway1981 on 2008-02-26
pc@pc-desktop:~$ touch /media/sda1/testing
pc@pc-desktop:~$ touch /media/wayway/testing
touch: cannot touch `/media/wayway/testing': No such file or directory
pc@pc-desktop:~$ touch /media/sda1/testingtouch /media/sda1/testing
pc@pc-desktop:~$ touch /media/sda1/testing
pc@pc-desktop:~$ sudo umount /dev/sda1
pc@pc-desktop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
pc@pc-desktop:~$ sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
pc@pc-desktop:~$ ls -la /media/sda1touch /media/sda1/testing
ls: /media/sda1touch: No such file or directory
-rwxrwxrwx 1 root root 0 2008-02-26 22:25 /media/sda1/testing
pc@pc-desktop:~$ touch /media/sda1/testing
pc@pc-desktop:~$

---

### Post by rbc on 2008-02-26
Can't help you with formatting but if you just want to delete something, try this in terminal:
pmount /dev/sda1 /media/<whateveryouwant>. The whateveryouwant directory in /media is going to have to be something other than sda1

---

### Post by taurus on 2008-02-26
> **wayway1981 said:**
> pc@pc-desktop:~$ touch /media/sda1/testing
pc@pc-desktop:~$ touch /media/wayway/testing
touch: cannot touch `/media/wayway/testing': No such file or directory
pc@pc-desktop:~$ touch /media/sda1/testingtouch /media/sda1/testing
pc@pc-desktop:~$ touch /media/sda1/testing
pc@pc-desktop:~$ sudo umount /dev/sda1
pc@pc-desktop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
pc@pc-desktop:~$ sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
pc@pc-desktop:~$ ls -la /media/sda1touch /media/sda1/testing
ls: /media/sda1touch: No such file or directory
-rwxrwxrwx 1 root root 0 2008-02-26 22:25 /media/sda1/testing
pc@pc-desktop:~$ touch /media/sda1/testing
pc@pc-desktop:~$

I think you are confused between /media/sda1 & /media/wayway.  Your external harddrive is now mounted to /media/sda1 so you need to access it from there, NOT /media/wayway.

And since you just created a new file called testing in /media/sda1, see if you can remove it with

```
rm /media/sda1/testing
```

---

### Post by wayway1981 on 2008-02-27
i have a backup of all this data off this 8gb microcenter flashdrive... i think the drive is shot on says is is has 84.83gb of data on it?:lolflag: and well not unmount no matter what you do i just going to take it back and get a new one


thank again for all the help

---

