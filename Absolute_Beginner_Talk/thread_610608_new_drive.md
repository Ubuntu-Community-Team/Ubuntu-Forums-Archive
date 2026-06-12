---
title: "new drive?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by dysolve on 2007-11-12
Hello all,
I finally got my server running how I want it so it time to mount a few extra drives. now I formated the drive and fdisk'ed it but I can not mount it . I am not sure what to try next

[FONT="Arial"][SIZE="1"][COLOR="Red"]fdisk -l

Disk /dev/sda: 18.2 GB, 18200739840 bytes
255 heads, 63 sectors/track, 2212 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2114    16980673+  83  Linux
/dev/sda2            2115        2212      787185    5  Extended
/dev/sda5            2115        2212      787153+  82  Linux swap / Solaris

Disk /dev/sdb: 18.2 GB, 18200739840 bytes
255 heads, 63 sectors/track, 2212 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2212    17767858+  83  Linux[/COLOR][/SIZE][/FONT]

its /dev/sbd1
so what do I do next to get it to work??

when i try to access the drive I get the following
[COLOR="Red"][SIZE="1"]
root@server1:~# /dev/sdb1
-bash: /dev/sdb1: Permission denied[/SIZE][/COLOR]
thanks!

---

### Post by kpkeerthi on 2007-11-12
Before you access the drive, you need to mount it.

make a folder where you want it mounted.

```

sudo -su
mkdir /media/data

```

Then mount it

```

mount -t ext3  /dev/sdb1 /media/data

```

If you would like to have it mounted permanently, you need to add an entry to /etc/fstab
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab 

```

Add the below line to the end of the file. Save and reboot.

```

/dev/sdb1   /media/data   ext3  defaults    0   0

```

You can now cd to /media/data or use nautilus to access the files.

---

### Post by insane_alien on 2007-11-12
you fdisk'd it but you failed to give it a filesystem.

```
mk2fs -j /dev/sdb
```  or something to that effect. that'll make an ext3 filesystem

---

### Post by dysolve on 2007-11-13
thanks for the help that sorted it out!!

---

