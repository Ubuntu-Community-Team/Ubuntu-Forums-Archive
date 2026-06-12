---
title: "lost write permission on hd"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by yard on 2006-12-16
I've lost write privelages to my second harddrive after restarting today.  If I right click on the folder it's mounted to and go to properties, it shows I do have read and write privelages.  I am, however, not able to create any new folders on that drive, and when I try to resume a torrent  which was active less than an hour ago I get an error 30, read-only message.  I have not recently made any changes to the system. Fstab line for that hd: 

/dev/hdb1     /a_media     vfat     defaults,umask=00000  0     0

I'm kind of new and don't really remember why I used this particular line (i.e. umask=00000  0  0)  but its been working fine for a while now.  Any suggestion?

---

### Post by taurus on 2006-12-16
You have way too many 0's for the umask...  Change your /etc/fstab and remove two of them so it would look something like this now.

```
/dev/hdb1  /a_media  vfat  defaults,umask=000  0  0
```

---

### Post by yard on 2006-12-17
okay, drop two 0s from the fstab, restarted, and everything wsa fine for about 5-10 minutes.  then back to same problem...

---

### Post by taurus on 2006-12-17
What's the output of this command then?

```
sudo fdisk -l
```

---

### Post by yard on 2006-12-17
Disk /dev/hda: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2427    19494846   83  Linux
/dev/hda2            2428        2534      859477+   5  Extended
/dev/hda5            2428        2534      859446   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321    b  W95 FAT32

---

### Post by taurus on 2006-12-17
What about 

```
ls -la  /
cat  /etc/fstab
```

---

### Post by yard on 2006-12-17
ls -la  /:
total 136
drwxr-xr-x  22 root root  4096 2006-11-11 23:42 .
drwxr-xr-x  22 root root  4096 2006-11-11 23:42 ..
drwxrwxrwx  11 root root 16384 1969-12-31 19:00 a_media
drwxr-xr-x   2 root root  4096 2006-11-28 16:01 bin
drwxr-xr-x   3 root root  4096 2006-12-14 12:29 boot
drwxr-xr-x  15 root root 15020 2006-12-17 03:24 dev
drwxr-xr-x 111 root root  4096 2006-12-17 03:17 etc
drwxr-xr-x   3 root root  4096 2006-11-11 23:05 home
drwxr-xr-x   2 root root  4096 2006-08-05 19:19 initrd
lrwxrwxrwx   1 root root    29 2006-11-11 23:20 initrd.img -> boot/initrd.img-2.6.15-27-386
lrwxrwxrwx   1 root root    29 2006-11-11 23:00 initrd.img.old -> boot/initrd.img-2.6.15-26-386
drwxr-xr-x  19 root root  4096 2006-11-11 23:07 lib
drwxr-xr-x   2 root root 49152 2006-11-11 23:00 lost+found
drwxr-xr-x   3 root root  4096 2006-12-16 22:44 media
drwxr-xr-x   2 root root  4096 2006-05-22 10:00 mnt
drwxr-xr-x   2 root root  4096 2006-08-05 19:19 opt
dr-xr-xr-x 119 root root     0 2006-12-17 03:15 proc
drwxr-xr-x   7 root root  4096 2006-11-12 00:55 root
drwxr-xr-x   2 root root  8192 2006-11-22 13:26 sbin
drwxr-xr-x   2 root root  4096 2006-08-05 19:19 srv
drwxr-xr-x  10 root root     0 2006-12-17 03:15 sys
drwxrwxrwt  10 root root  4096 2006-12-17 21:00 tmp
drwxr-xr-x  11 root root  4096 2006-08-05 19:20 usr
drwxr-xr-x  14 root root  4096 2006-08-05 19:32 var
lrwxrwxrwx   1 root root    26 2006-11-11 23:20 vmlinuz -> boot/vmlinuz-2.6.15-27-386
lrwxrwxrwx   1 root root    26 2006-11-11 23:00 vmlinuz.old -> boot/vmlinuz-2.6.15-26-386

and cat  /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0

/dev/hdb1     /a_media     vfat     defaults,umask=000  0     0

#192.168.0.15:/home/daniel/Desktop/HardDrives/Stuff /home/shawn/Desktop/deez nfs defaults 0 0

#192.168.0.15:/home/daniel/Desktop/HardDrives/Extra_Stuff /home/shawn/Desktop/mo_deez nfs defaults 0 0

#192.168.0.15:/home/daniel/Desktop/HardDrives/Even_More_Stuff /home/shawn/Desktop/even_mo_deez nfs defaults 0 0

#192.168.0.13:/home/htpc/Desktop/stuff /home/shawn/Desktop/htpc nfs defaults 0 0
 
(All the stuff at the bottom with the # are for two other computers my brother has taken home with him for the holidays)

---

