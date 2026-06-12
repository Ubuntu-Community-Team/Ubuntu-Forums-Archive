---
title: "hardrive disappear"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by m_o_b on 2007-07-05
I installed another Linux (Mandriva) to try both Gnome and KDE but when the computer boots it doesn't show ubuntu only mandriva.

and the devices shows mandriva device only not the ubuntu's

how can i mount it.

---

### Post by Cypher on 2007-07-05
You could've just as easily installed KDE on your Ubuntu installation and switched between Gnome and KDE without installing an entirely new OS just to try out KDE.

But anyway..how did your partition the hard drive for Mandriva?

---

### Post by eoghanmurray on 2007-07-05
Did you install Mandriva on the same hard drive or partition as Ubuntu?

---

### Post by m_o_b on 2007-07-05
i installed it on other partition and on the KDE storage devices it shows that it's mounted but it doesn't show on the devices icons on the desktop it's not showing. 

and i can't boot it to ubuntu because it doesn't show it when the computer boots.

and i also used on linux swap for both partitions. (which is 1 GB)

---

### Post by Cypher on 2007-07-05
Other partition?

Please open a terminal and show the output of
```

sudo fdisk -l
mount
df -h

```

---

### Post by m_o_b on 2007-07-05
```

sudo fdisk -l
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2562    20579233+   c  W95 FAT32 (LBA)
/dev/hda2   *        2563        5639    24716002+  83  Linux
/dev/hda3            5640        7154    12169237+   5  Extended
/dev/hda4            7155        7294     1124518+  82  Linux swap / Solaris
/dev/hda5            5640        7154    12169206   83  Linux
[root@localhost mohammed]# mount
/dev/hda2 on / type ext3 (rw,noatime)
none on /proc type proc (rw)
/dev/hda1 on /mnt/windows type vfat (rw,umask=0,iocharset=utf8)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda5 on /kubuntu type ext3 (rw)
[root@localhost mohammed]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              24G  3.4G   19G  16% /
/dev/hda1              20G  5.6M   20G   1% /mnt/windows
/dev/hda5              12G  2.9G  8.1G  26% /kubuntu

```

---

### Post by Cypher on 2007-07-05
OK, so you are currently booted into Mandriva? And was Ubuntu installed to /dev/hda5 before or was it /dev/hda2? If /dev/hda2, then you've overwritten Ubuntu. 

Can you do the following
```

sudo mkdir /mnt/test
sudo mount -text3 /dev/hda5 /mnt/test
ls -l /mnt/test

```
See what is in /dev/hda5..

---

### Post by m_o_b on 2007-07-05
here is the outcome
```

total 88
drwxr-xr-x   2 root root  4096 Jul  1 17:16 bin/
drwxr-xr-x   3 root root  4096 Jul  1 16:12 boot/
lrwxrwxrwx   1 root root    11 Jul  1 17:02 cdrom -> media/cdrom/
drwxr-xr-x   5 root root  4096 Apr 17 23:30 dev/
drwxr-xr-x 109 root root  4096 Jul  4 20:58 etc/
drwxr-xr-x   3 root root  4096 Jul  1 17:12 home/
drwxr-xr-x   2 root root  4096 Apr 17 23:15 initrd/
lrwxrwxrwx   1 root root    33 Jul  1 16:12 initrd.img -> boot/initrd.img-2.6.20-16-generic
lrwxrwxrwx   1 root root    33 Jul  1 17:15 initrd.img.old -> boot/initrd.img-2.6.20-15-generic
drwxr-xr-x  16 root root  4096 Jul  1 17:16 lib/
drwx------   2 root root 16384 Jul  1 17:02 lost+found/
drwxr-xr-x   4 root root  4096 Jul  4 20:58 media/
drwxr-xr-x   2 root root  4096 Apr 12 05:11 mnt/
drwxr-xr-x   2 root root  4096 Apr 17 23:15 opt/
drwxr-xr-x   2 root root  4096 Apr 12 05:11 proc/
drwxr-xr-x  19 root root  4096 Jul  3 20:37 root/
drwxr-xr-x   2 root root  4096 Jul  1 16:11 sbin/
drwxr-xr-x   2 root root  4096 Apr 17 23:15 srv/
drwxr-xr-x   2 root root  4096 Apr  4 06:47 sys/
drwxrwxrwt   7 root root  4096 Jul  4 20:58 tmp/
drwxr-xr-x  11 root root  4096 Apr 17 23:17 usr/
drwxr-xr-x  15 root root  4096 Apr 17 23:28 var/
lrwxrwxrwx   1 root root    30 Jul  1 16:12 vmlinuz -> boot/vmlinuz-2.6.20-16-generic
lrwxrwxrwx   1 root root    30 Jul  1 17:15 vmlinuz.old -> boot/vmlinuz-2.6.20-15-generic

```

and i did installed it before mandriva. but i nstalled mandriva in different partition and ubuntu is on hda5

---

