---
title: "Partitions"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by bparham on 2007-03-05
Ok, I've got a goofy question, but I can't seem to find the answer anywhere. How do you check you system to see if Home is on a separate partition? I show three separate partitions on my Linux drive, but I'm not sure where home resides.

---

### Post by taurus on 2007-03-05
Applications -> Accessories -> Terminal
```
df -h
```

p.s.  Can't view the screenshot, toooooo small.

---

### Post by bparham on 2007-03-05
Here is the output from running df -h and fdisk -l; can someone help me interpret. I think the line in bold is my home partition, but i don't know for sure. 

brad@brad-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun                252M  128K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  234M   8% /lib/modules/2.6.17-11-386/volatile
brad@brad-desktop:~$ fdisk -l
brad@brad-desktop:~$ sudo fdisk -l
oPassword:

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        4392    35238577+   7  HPFS/NTFS
/dev/hda3            4393        4862     3775275   db  CP/M / CTOS / ...

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4676    37559938+  83  Linux
**/dev/hdb2            4677        4863     1502077+   5  Extended**
/dev/hdb5            4677        4863     1502046   82  Linux swap / Solaris

---

### Post by bparham on 2007-03-05
Here is the output of ```
cd / ls -la
```

```
total 136
drwxr-xr-x  23 root root  4096 2007-03-02 07:23 .
drwxr-xr-x  23 root root  4096 2007-03-02 07:23 ..
drwxr-xr-x   2 root root  4096 2007-02-02 00:11 bin
drwxr-xr-x   3 root root  4096 2007-02-26 23:31 boot
lrwxrwxrwx   1 root root    11 2006-08-16 22:24 cdrom -> media/cdrom
drwxr-xr-x  15 root root 13740 2007-03-05 16:13 dev
drwxr-xr-x 135 root root  8192 2007-03-05 16:04 etc
drwxr-xr-x   4 root root  4096 2007-03-05 18:55 home
drwxr-xr-x   2 root root  4096 2006-05-30 20:49 initrd
lrwxrwxrwx   1 root root    29 2007-02-26 23:32 initrd.img -> boot/initrd.img-2.6.17-11-386
lrwxrwxrwx   1 root root    29 2006-10-30 22:48 initrd.img.old -> boot/initrd.img-2.6.17-10-386
drwxr-xr-x  21 root root  8192 2007-02-27 23:53 lib
drwxr-xr-x   2 root root 49152 2006-08-16 22:23 lost+found
drwxr-xr-x   3 root root  4096 2007-02-16 04:47 media
drwxr-xr-x   2 root root  4096 2006-05-22 10:00 mnt
drwxr-xr-x   3 root root  4096 2006-08-22 23:37 opt
dr-xr-xr-x 136 root root     0 2007-03-05 16:03 proc
drwxr-xr-x   2 root root  4096 2007-03-03 17:38 Recycled
drwxr-xr-x  18 root root  4096 2007-03-05 16:30 root
drwxr-xr-x   2 root root  8192 2007-02-26 23:30 sbin
drwxr-xr-x   2 root root  4096 2006-05-30 20:49 srv
drwxr-xr-x  11 root root     0 2007-03-05 16:03 sys
drwxrwxrwt  18 root root  4096 2007-03-05 16:46 tmp
drwxr-xr-x  13 root root  4096 2006-11-07 23:30 usr
drwxr-xr-x  15 root root  4096 2006-10-30 22:33 var
lrwxrwxrwx   1 root root    26 2007-02-26 23:32 vmlinuz -> boot/vmlinuz-2.6.17-11-386
lrwxrwxrwx   1 root root    26 2006-10-30 22:48 vmlinuz.old -> boot/vmlinuz-2.6.17-10-386
drwxr-xr-x   2 root root  4096 2006-10-05 20:28 Windows

```

It appears as though home is not on it's own partition. Am I correct in this assumption?

---

### Post by taurus on 2007-03-05
> **bparham said:**
> 
brad@brad-desktop:~$ sudo fdisk -l

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4676    37559938+  83  Linux
**/dev/hdb2            4677        4863     1502077+   5  Extended**
/dev/hdb5            4677        4863     1502046   82  Linux swap / Solaris

Sorry to tell you but you only have two partitions on your slave drive, /dev/hdb1 as / and /dev/hdb5 as swap.  /dev/hdb2 is your extended partition so technically you can't use it; that's why swap is your logical partition of that extended partition.  So, there is never a separate partition for /home.

---

### Post by bparham on 2007-03-05
That is what I was afraid of, thanks... 

I'll start working on other means of backing up my data before the install. This time I will make sure to create a separate partition for home.

---

