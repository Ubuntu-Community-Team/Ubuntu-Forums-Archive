---
title: "mounting fat32"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by rowster27 on 2006-10-23
i already tried this guide  but nothing happened [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

here is my sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4773    38339091   83  Linux
/dev/hda2            4774        4866      747022+   5  Extended
/dev/hda5            4774        4866      746991   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4865    39078081    c  W95 FAT32 (LBA)

how can i mount this spare drive?

---

### Post by jorn on 2006-10-23
Is it the /dev/hdb1 Fat32 you want to mount?

---

### Post by hillbilly on 2006-10-23
you could try 
```
sudo mount -t vfat /dev/hdb1 <mount point e.g. /mnt/FatDrive/One>
```

---

### Post by taurus on 2006-10-23
Edit your /etc/fstab from a terminal, Applications -> Accessories -> Terminal, as

```
gksudo gedit /etc/fstab
```
Then, add the following line to the end of it...

```

/dev/hdb1   /media/FAT32   vfat   defaults,umask=0000   0   0

```
Save it and run these two commands from the prompt.

```
sudo mkdir /media/FAT32
sudo mount -a
```
Now, your spare drive is in /media/FAT32 with read and write permissions...

---

### Post by bullgr on 2006-10-23
for mounting a disk you must first make a mount point.
for example:

> sudo mkdir /mnt/d

this command make a mount point to folder /mnt/d

after that edit the file /etc/fstab

> sudo gedit /etc/fstab

and add the line:

/dev/hdb1 /mnt/d vfat iocharset=utf8,umask=000 0 0

and that's it  :mrgreen: 
hope i help

---

### Post by Foudre on 2006-10-23
ok, what about NTFS?

---

### Post by rowster27 on 2006-10-23
> **taurus said:**
> Edit your /etc/fstab from a terminal, Applications -> Accessories -> Terminal, as

```
gksudo gedit /etc/fstab
```
Then, add the following line to the end of it...

```

/dev/hdb1   /media/FAT32   vfat   defaults,umask=0000   0   0

```
Save it and run these two commands from the prompt.

```
sudo mkdir /media/FAT32
sudo mount -a
```
Now, your spare drive is in /media/FAT32 with read and write permissions...

thank you so much taurus :)
thank you guys
thank you ubuntu
God bless you all :)

---

### Post by taurus on 2006-10-23
> **Foudre said:**
> ok, what about NTFS?

```

/dev/hdb1   /media/NTFS   ntfs   defaults,umask=0222   0   0

```

---

