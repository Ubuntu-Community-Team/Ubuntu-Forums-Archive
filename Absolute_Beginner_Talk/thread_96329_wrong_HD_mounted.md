---
title: "wrong HD mounted"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by ellwoodloc on 2005-11-28
i have ubuntu dual booting on my office comp with XP. i partioned/installed ubuntu on hdb. for some reason though, on my gnome desktop, hda(my windows installation) is showing up as the default hard drive and of course i am unable to access it. is there anyway to change this so that i can just have hdb my default drive?

thanks in advance again.
brittj

---

### Post by gord on 2005-11-28
please don't double post :)

also you are kinda vauge by what you meen by 'default' hard drive

---

### Post by ellwoodloc on 2005-11-28
heh sorry about that. 

lets see how i can organize this thought.

hda is where grub is installed and it also has my winXP installation(NTFS). its the primary master of the comp. hdb is where i installed all my ubuntu stuff. its using LFS. so essentially when Xwindows starts up, on my desktop i see the icon for hda1, which is my windows drive. i would like it to display hdb1, which i believe is the main partition where all my ubuntu files are, etc. heres this too if it'll help at all: 

```
brittj@brittj:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *        1242        2482     9968332+  83  Linux
/dev/hdb2             621        1241     4988182+   5  Extended
/dev/hdb5             622        1241     4980150   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
brittj@brittj:~$

```

hope that helps. no more double posting for me. 

thanks,
brittj

---

### Post by gord on 2005-11-28
the reason that its showing your windows drive is because ubuntu detected it and set it up for you, you can disable it by going into the configuration editor in the applications -> system tools menu. (goto apps->natilus uncheck volumes_visable). since your ubuntu drive is the root of the file system, your windows drive is mounted within it, and thus only the windows will show. 

you could allways just goto applications -> accessorys -> file manager, right click on the filemanager icon and press 'add application to desktop'. you'll be able to access your root filesystem (hdb1) from there.

---

