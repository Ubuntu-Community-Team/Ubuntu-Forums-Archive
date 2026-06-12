---
title: "Mount /dev/sda1"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by falk3r on 2007-03-24
I'm having a hell of a time seeing my secondary, NTFS HDD. When I use:

```
sudo fdisk -l
```

I see:

```
 Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9729    78148161   83  Linux

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30254   243015223+   7  HPFS/NTFS
/dev/sda2           30255       30515     2096482+  82  Linux swap / Solaris

```

That /dev/sda1 is the HDD I want to be able to access. I've tried:
```

sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

And see:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Any suggestions would be GREAT.

Thank you for your time,
 - falk3r

---

### Post by Pett on 2007-03-24
Try to type just this:
```
sudo mount /dev/sda1 /media/windows/
```
Or if you want this partition to be mounted at startup then edit /etc/fstab and add there this line:
```
/dev/sda1  /media/windows  ntfs  defaults,user,umask=0222,nls=utf8  0  0
```

---

### Post by falk3r on 2007-03-24
Great, it mounted... but when I navigate to it via Nautilus, I receive the error message :

> The folder contents could not be displayed.

You do not have the permissions necessary to view the contents of "windows".

How do I obtain the necessary permissions?

---

### Post by Pett on 2007-03-24
It's because only root has permissions to read the content. Try to read through the manual of mount..
```
man mount
```
Or do it with /etc/fstab as i wrote. You won't need to mount it on every startup.

---

### Post by Bachstelze on 2007-03-24
Run the first line you tried but put the mountpoint at the end, like this :

```
sudo mount /dev/sda1 -t ntfs -o nls=utf8,umask=0222 /media/windows
```

---

### Post by Pett on 2007-03-24
Or type:
```
sudo mount -o defaults,user,umask=0222,nls=utf8 /dev/sda1 /media/windows
```
It should do the same as I have written to /etc/fstab, so you have permissions to read it

---

### Post by Bachstelze on 2007-03-24
defaults and user should not be put in a mount command, only in fstab.

---

### Post by Pett on 2007-03-24
sorry, my bad

---

### Post by falk3r on 2007-03-25
Thank you HymnToLife,

Now, how would I modify these terminal commands to mount an ext3 formated harddrive?

```
sudo mount -t ext3 /dev/sdb1 /media/xternal893
```

Mounts it, but again I do not have proper permissions, and the same code you suggested above apparently has extra options that only pertain to NTFS.

If I reformatted in FAT, how would this command change?

Thank you for your time,
 - falk3r

---

### Post by lunamystry on 2007-08-27
i need to know how to mount my /dev/sda1 which is Kubuntu feisty fawn on the gusty. When I am in Feisty I just use mount /dev/sda1 and it works. I reckon now I have to create a new directory because with festy I installed gparted and it created an irritating directory on my home folder <mount point> and after that i could mount my Gusty hard drive. Now I am wondering how to go forward from 

sudo mkdir /media/ubuntu 

which is what i thought i would do just follow the above instructions and change all the windows words to ubuntu. I then remembered that the two partitions are not the same so I think i would like my own instaructions please if someone would please. 

Thank you 

I just got it right, i used sudo mount /dev/sda1 /media/ubuntu

---

