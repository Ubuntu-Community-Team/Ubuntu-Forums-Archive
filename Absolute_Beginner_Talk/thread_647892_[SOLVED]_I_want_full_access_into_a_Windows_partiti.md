---
title: "[SOLVED] I want full access into a Windows partition"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by iamclueless on 2007-12-22
ok almost there...

got my Windows D:\ partition hard drive mounted.

however i only have read permission on it. So i copy files from it but i cannot delete or copy to it.

root has the read and write permission.. i want it

i can imagine that in the terminal ill have to do sudo something in order to change this

please advice

thanks

---

### Post by kevin11951 on 2007-12-22
> **iamclueless said:**
> ok almost there...

got my Windows D:\ partition hard drive mounted.

however i only have read permission on it. So i copy files from it but i cannot delete or copy to it.

root has the read and write permission.. i want it

i can imagine that in the terminal ill have to do sudo something in order to change this

please advice

thanks

not exactly sure what you mean? but if you want to set permissions in ubuntu for anything do:
```
sudo chmod 777 (for unlimited access to file(s) <insert file or drive here>
```

thats the best i can do, maybe someone else can explain it better.

---

### Post by jflaker on 2007-12-22
try ```
sudo nautilus
```

This will put you into super user mode in nautilus and you may be able to delete at that point.

What version of Ubuntu?

---

### Post by wormser on 2007-12-22
You did not say what you are running.  You might need to install ntfs-3g and ntfs-config.

```
sudo apt-get install ntfs-3g ntfs-config
```

---

### Post by jflaker on 2007-12-22
> **kevin11951 said:**
> not exactly sure what you mean? but if you want to set permissions in ubuntu for anything do:
```
sudo chmod 777 (for unlimited access to file(s) <insert file or drive here>
```

thats the best i can do, maybe someone else can explain it better.

not on a NTFS partition (as far as I know, anyway)

---

### Post by iamclueless on 2007-12-22
quick responses wow

ok im running Xubuntu

I got it!!!!

went into fstab and wrote it in myself... well cut and past job from 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
and i just changed the names

thanks

---

### Post by Tyke91 on 2007-12-22
is it ntfs or fat32?
do you have ntfs-3g?
what version of Xubuntu are you using?

EDIT: nvm... ninja'd

---

### Post by jflaker on 2007-12-22
> **iamclueless said:**
> quick responses wow
..Snipped

And it is why Linux will always be better!

---

### Post by quandary on 2007-12-22
It's quite easy, however, as you are not logged in as root, it's a bit tricky ;-)

Do it like this:
On terminal, type:
```

fdisk -l

```

This shows you something like this:
```

root@googlebot:~# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd296e65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/sda2            2933        7296    35053120    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08c660a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60427   485379846   83  Linux
/dev/sdb2           60428       60801     3004155    f  W95 Ext'd (LBA)
/dev/sdb5           60428       60801     3004123+  82  Linux swap / Solaris
root@googlebot:~# 


```

You see from there, that /dev/sda1 and /dev/sda2 are NTFS partitions, so windows.

Now say, you want to mount sda1, then do the following on the command line:
```

sudo mkdir /media/blabla
sudo mount /dev/sda1 /media/blabla -o rw

```

Now type:
```

sudo nautilus

```

If you've finished, type:
```

sudo umount /media/blabla

```

---

