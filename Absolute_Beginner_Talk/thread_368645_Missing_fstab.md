---
title: "Missing fstab"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Platinum89 on 2007-02-23
I've reviewed many threads that refer to NFTS format, but not the FAT32. I followed the link  to "Mounting Windows Partitions in Ubuntu" as well. Unfortunately, that's where I become lost in the wilderness. The problem is, the FSTAB file is missing. For some reason, it was never created and I'm not sure what to put in one. This is the only problem I have left and I urgently need to access the Win98SE drives for various documents/files. Below is what the sudo fdisk -l reports.

Disk /dev/hda: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1244     9992398+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4863    39062016    c  W95 FAT32 (LBA)
/dev/hdb2   *        4864        9871    40226760   83  Linux
/dev/hdb3            9872        9964      747022+   5  Extended
/dev/hdb5            9872        9964      746991   82  Linux swap / Solaris

I need to access the /dev/hda1 and /dev/hdb1. What would the FSTAB file look like so I can mount these and access them? Your help is greatly appreciated.

---

### Post by AtrejuT on 2007-02-23
are you sure the file is missing? because it _really_ should be there.

what does 
```

ls -al /etc/* | grep fstab

```

give you?
(take care of capitalization, or rather, no capitalization...


atreju

---

### Post by taurus on 2007-02-23
Are you sure you don't have /etc/fstab?  Otherwise, you wouldn't be able to boot to Ubuntu.

Edit /etc/fstab

Applications -> Accessories -> Terminal
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
/dev/hdb1   /media/hdb1   vfat   iocharset=utf8,umask=000   0   0

```
Save it.  Now, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/hdb1
sudo mount -a
df -h
```

---

### Post by Platinum89 on 2007-02-23
This what I receive from the terminal....

sudo /etc/fstab /etc/fstab.bak

sudo: /etc/fstab: command not found


I know this is weird....

The other command someone suggested gives the following...
 ls -al /etc/*|grep fstab
-rw-r--r--  1 root   root       534 2007-02-19 03:40 /etc/fstab


I'm getting slivers in my fingers from scratching my balding head on this one.

---

### Post by jkeyes0 on 2007-02-23
> **Platinum89 said:**
> This what I receive from the terminal....

sudo /etc/fstab /etc/fstab.bak

sudo: /etc/fstab: command not found


I know this is weird....

The other command someone suggested gives the following...
 ls -al /etc/*|grep fstab
-rw-r--r--  1 root   root       534 2007-02-19 03:40 /etc/fstab


I'm getting slivers in my fingers from scratching my balding head on this one.

I think the sudo /etc/fstab /etc/fstab.bak may have been a mistype. 

Try "sudo cp /etc/fstab /etc/fstab.bak". 

This is making a backup copy of your fstab file in case something goes wrong in the editing.

---

### Post by Platinum89 on 2007-02-23
I finally got it. I remember looking for the fstab file this morning and it couldn't find it. Regardless, I rebooted the system and looked again and it was there. I've edited and followed the instructions provided by taurus and I can now access the drives required. Many thanks to all. I can now get back to work \\:D/

---

