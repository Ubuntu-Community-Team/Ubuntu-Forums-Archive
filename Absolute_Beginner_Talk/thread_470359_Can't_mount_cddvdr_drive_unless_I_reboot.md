---
title: "Can't mount cd/dvdr drive unless I reboot"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-06-10
I can't seem to be able to mount cd/dvdr drive unless I reboot.

It gives me error; **Unable to mount cd/dvdr drive; there is probably no media in the drive.**

What can I do to correct this? :confused:

---

### Post by Ek0nomik on 2007-06-11
What are you currently doing to mount your drive?  Are you typing in a command in the terminal?

---

### Post by discmaster on 2007-06-11
I am right clicking the drive in "computer" to try & get it to mount. Also, I forgot to mention that I have 2 identical drives in this pc (Benq 1640), & in computer, only 1 is listed?

---

### Post by Ek0nomik on 2007-06-11
Can you please post the output of these commands (Accesories/Terminal)

```
sudo fdisk -l
```

and ```
sudo mount
```

and ```
cat /etc/fstab
```

---

### Post by discmaster on 2007-06-12
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648        6079    19535040   83  Linux
/dev/sda3            6080        7991    15358140   83  Linux
/dev/sda4            7992       30401   180008325    5  Extended
/dev/sda5            7992        8257     2136613+  82  Linux swap / Solaris
/dev/sda6            8258       30401   177871648+  83  Linux
tr@tr-desktop:~$ 



tr@tr-desktop:~$ sudo mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
/dev/sda6 on /media/sda6 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
tr@tr-desktop:~$ 


tr@tr-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=e0c5c3c2-31d0-494e-a59a-7f5afd71c22f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=f5e28123-e525-4e5e-9fe8-6d79170790e2 /home           ext3    defaults        0       2
# /dev/sda1
UUID=f2884278-3e06-4fe8-af01-6efb38457b1b /media/sda1     ext3    defaults        0       2
# /dev/sda6
UUID=2d1e5ae4-97f2-4287-8245-ba22402ccb89 /media/sda6     ext3    defaults        0       2
# /dev/sda5
UUID=e2202547-6119-4e52-9e0a-a0efa81cb195 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
tr@tr-desktop:~$

---

### Post by Ek0nomik on 2007-06-13
Try

```
sudo mount /dev/hda /media/cdrom0
```

Do you get any output?

---

