---
title: "messed up really bad, need help!"
date: 2007-08-15
forum: Apple Intel Users
---

### Post by andrewbossie on 2007-08-15
i have no idea how i did it, but i seemed to have messed up my xorg file and now when i boot ubuntu i get the "failed xserver" screen, even worse is when i try and reconfigure or change anything, i get an error that says that my filesystem is read-only. im afraid my fstab is messed up too. i would really like to fix this without reinstalling, so if anyone can help me i would greatly appreciate it!!!!


-thanks

---

### Post by benanzo on 2007-08-15
can you post both your **/etc/X11/xorg.conf** and your **/etc/fstab** as well as your partition table?

you can get your partition table by doing:
```

sudo parted /dev/sda
print
quit

```

---

### Post by cyberdork33 on 2007-08-15
> **benanzo said:**
> can you post both your /etc/xorg.conf and your fstab?

Yea, and whatever the xorg error actually says would be helpful too.

---

### Post by andrewbossie on 2007-08-16
my parted print output is :

Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start     End       Size       Type      File System   Flags
1           32.3kb  59.0GB 59.0GB  primary  ext3
3           59.0GB 60.0GB 1011MB primary  linux-swap

fstab:


proc /proc proc defaults 0 0
# Entry for /dev/sda1 : 
UUID=e6674779-cd9b-4bbd-9f71-83c092b11470 / ext3 defaults,errors=remount 0 1
#Entry for /dev/sda3 : 
UUID=aa5c991d-913e-4560-a426-8eb30053d886 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user , noauto 0 0

---

