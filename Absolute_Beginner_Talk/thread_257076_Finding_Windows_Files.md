---
title: "Finding Windows Files"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Chris85r on 2006-09-14
I am still a newbie to linux so bear with me.  I am currently running Kubuntu , which is dual booted with windows xp. I have seperate hard drive partitions.  Is there any way to play my mp3 files that are on my windows partition in linux?  Thankx

---

### Post by Najand on 2006-09-14
If you have done the installation correctly you can see the windows drive on your Desktop, as the boot process would automount other partitions of your hard disk automatically. (You may also find it at /media/Windows or something similar. You can use (just read and no write in case of ntfs) files of your windows partition.
If you cannot find it, please run:
```

sudo fdisk -l

```
and
```

mount

```
in console (terminal) and copy and paste the output here...

---

### Post by Chris85r on 2006-09-14
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         638     5124703+  12  Compaq diagnostics
/dev/sda2   *         639        7583    55785712+   7  HPFS/NTFS
/dev/sda3            7584       14305    53994465   83  Linux
/dev/sda4           14306       14593     2313360    5  Extended
/dev/sda5           14306       14593     2313328+  82  Linux swap / Solaris
christopher@christopher-laptop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)

---

### Post by Chris85r on 2006-09-14
what do i do now that did nothing?

---

### Post by Najand on 2006-09-14
Well, It seems that it has not been mounted to your harddisk.
Then try to do the following step by step:
1. Make sure it has not been mounted by running this in the terminal:
```

sudo umount /dev/sda2

```
2.Make a Directory for mounting Windows in it. To  do that run:
```

sudo mkdir /media/Windows

```
3. Try to edit /etc/fstab using nano:
```

sudo nano -B /etc/fstab

```
4. Add the following line to fstab:
```

/dev/sda2 /media/Windows ntfs nls=utf8,umask=0222 0 0

```
[COLOR="Red"]Caution: If fstab has a line starting with /dev/sda2 delete it using (Ctrl+k) before adding new line.[/COLOR]
5. Save (Control-X, Y, Enter)
6. mount all partitions:
sudo mount -a

---

### Post by TooRight on 2006-09-14
Your instructions worked great on my system... thanks sooo much for posting them!! :D

---

### Post by Najand on 2006-09-15
You are welcome.

---

### Post by Chris85r on 2006-09-15
Great set of directions thank you very much.

---

