---
title: "AMD64 - Storage Drive adice - &quot;Can not mount drive&quot;"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by TriZz on 2006-08-19
I'm dual-booting with XP.

I have a 200GB Maxtor that I use as a "storage drive".  Right now, it's empty.  I just formatted with windows to NFTS.  

...does anyone know how I can get Ubuntu (AMD64) to mount that drive?  If I click on it from the "computer" place - it says that it is unable to mount the drive.

Thanks!

---

### Post by GeekSpeek'r on 2006-08-19
make sure the drive is shared in Windows

goto: Places --> Connect to Server --> and specify what you want to do

hope it helps

---

### Post by TriZz on 2006-08-19
No such luck.

...any further suggestions?

---

### Post by taurus on 2006-08-19
If you want to use that drive as a storage drive, then maybe you want to format it as fat32/vfat so you can write to it from both Ubuntu and XP.  Writing to NTFS from Ubuntu is not highly recommand because you can trash the whole drive!!!  Otherwise, run these two commands at the prompt, assuming that it is the second harddrive on your system.

```

sudo mkdir /media/storage
sudo mount -t ntfs /dev/hdb1 /media/storage

```

---

### Post by TriZz on 2006-08-19
What would in input if I wanted to format it as fat32/vfat?  would it change to...?

```
sudo mkdir /media/storage
sudo mount -t fat32 /dev/hdb1 /media/storage
```

---

### Post by TriZz on 2006-08-19
.

---

### Post by taurus on 2006-08-19
```

sudo mkdir /media/storage
sudo mount -t vfat /dev/hdb1 /media/storage

```

---

### Post by TriZz on 2006-08-19
That didn't work out too well - here was the output:

```
trizz@ubuntu:~$ sudo mkdir /media/storage
Password:
trizz@ubuntu:~$ sudo mount -t vfat /dev/hdb1 /media/storage
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

trizz@ubuntu:~$
trizz@ubuntu:~$ dmesg | tail
[  103.498950] Bluetooth: L2CAP ver 2.8
[  103.498954] Bluetooth: L2CAP socket layer initialized
[  103.501820] Bluetooth: RFCOMM socket layer initialized
[  103.501835] Bluetooth: RFCOMM TTY layer initialized
[  103.501837] Bluetooth: RFCOMM ver 1.7
[  240.813529] ISO 9660 Extensions: Microsoft Joliet Level 3
[  240.868329] ISO 9660 Extensions: RRIP_1991A
[  241.041702] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  273.985314] FAT: bogus number of reserved sectors
[  273.985387] VFS: Can't find a valid FAT filesystem on dev hdb1.
trizz@ubuntu:~$
```

Perhaps this will help...?

---

### Post by taurus on 2006-08-19
Did you format /dev/hdb1 as fat32 or did you leave it as NTFS?  Replace the "vfat" with "ntfs" and see what happens.  Otherwise, 

```
dmesg | tail
```

---

### Post by TriZz on 2006-08-19
> **taurus said:**
> Did you format /dev/hdb1 as fat32 or did you leave it as NTFS?  Replace the "vfat" with "ntfs" and see what happens.  Otherwise, 

```
dmesg | tail
```

That worked well - I can access from home/media/storage ...sorta.

It only lets access to root.  I don't know how to let it know that I'm the root person from the file system.

Also, if I wanted to re-format the drive as vfat, or fat32 (if there's a difference) - how would I do that?  I formatted the drive in Windows and it only gave me the option of NTFS.

Thanks for all your help taurus, I really do appreciate all this.

---

### Post by taurus on 2006-08-19
So /dev/hdb1 is NTFS!!!  If you want to format it as vfat (or fat32), then you can boot your machine with desktop CD or LiveCD and use gparted to format it as vfat.  Then, you modify your /etc/fstab to include this line to it, /dev/hdb1, will be mounted automatically upon boot...

```

/dev/hdb1   /media/storage   vfat   defaults,umask=0000   0   0

```

---

