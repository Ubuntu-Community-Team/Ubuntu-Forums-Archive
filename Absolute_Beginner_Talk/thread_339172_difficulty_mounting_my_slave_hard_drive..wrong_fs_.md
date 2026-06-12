---
title: "difficulty mounting my slave hard drive..wrong fs type?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by subliminalrehab on 2007-01-15
within my /etc/fstab setup, i have this line inputted for my slave drive...

> /dev/hdb1 /mnt/xxtra ext3 defaults,errors=remount 0

the "/mnt/xxtra" is an existing folder on the primary hard drive and has been mounted before to this location. also, i have since already moved data onto the drive when i previously had it mounted. when i rebooted, i guess it didn't mount so i also need help getting it to mount upon reboot as well. :confused:

when i run a "sudo mount -a", this is what i get. ..

```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

any suggestions? :-k 

thanks in advance.

---

### Post by taurus on 2007-01-15
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

p.s.
```
/dev/hdb1   /mnt/xxtra   ext3   defaults   0   1
```

---

### Post by subliminalrehab on 2007-01-15
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

p.s.
```
/dev/hdb1   /mnt/xxtra   ext3   defaults   0   1
```

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7297    58613121   83  Linux

```

it's there, but not sure what that means in its entirety.


edit: whoops, just saw your edit. let me try that

---

### Post by subliminalrehab on 2007-01-15
thanks taurus! :mrgreen:

that did it. will that also enable the drive to mount upon boot or is there something else i have yet to do?

---

### Post by taurus on 2007-01-15
It will be mounted automatically each time you boot into Ubuntu.  No need to do or run anything extra before you use it (unless it's the permission thing).

---

### Post by subliminalrehab on 2007-01-15
thanks again for the help! i look forward to learning a lot more about ubuntu this year. i've heard good things about this forum. :D

---

### Post by taurus on 2007-01-15
Have fun.

---

