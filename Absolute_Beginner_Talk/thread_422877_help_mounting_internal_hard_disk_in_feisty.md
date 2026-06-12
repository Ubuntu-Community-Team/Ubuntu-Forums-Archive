---
title: "help mounting internal hard disk in feisty"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by kditty on 2007-04-25
i upgraded to feisty via format + install. i have a internal drive i used with dapper, when i first loaded feisty it was in the tree in nautilus, after a reboot its not. i need help mounting this drive because all of my backup files are loaded on there as well as music media nad pictures. any help is much appriciated thanks a lot.

---

### Post by bobbocanfly on 2007-04-25
Not sure whether this will work but in Terminal type (If FS is NTFS, not sure about other Fs's)

```
mount -t ntfs /dev/<whatever partition its> /mnt/<destination mount point>
```

---

### Post by marko_4454 on 2007-04-25
> **bobbocanfly said:**
> Not sure whether this will work but in Terminal type (If FS is NTFS, not sure about other Fs's)

```
mount -t ntfs /dev/<whatever partition its> /mnt/<destination mount point>
```

I dont think that the format he is using is ntfs because he used it for dapper. 
So I think it can just be something like this:

```
sudo mount /dev/<Partition> /media/<Destination point>
```

If you wanna load it every time it the computer starts, you need to edit fstab.

---

### Post by kditty on 2007-04-25
neither one fo these worked. is there a how to on mounting an internal drive on boot for feisty?

---

### Post by Nythain on 2007-04-25
read up on editing the fstab appropriately for the filesystem of the partition to get it to mount automatically every time you boot... usually something like this in your /etc/fstab
```

/dev/hdb1 (or whatever partition it is)      /mountpoint (wherever you want to mount it)    ext3 (or whatever filesystem the partition uses)    defaults (and any other options, though defaults should be enough)      0      2

```should do the trick

make sure you actually create the mountpoint... like if you want it mounted at /backup then you have to create the folder /backup ahead of time or there's not actually going to be a place for the partition to be mounted

---

### Post by marko_4454 on 2007-04-25
> **kditty said:**
> neither one fo these worked. is there a how to on mounting an internal drive on boot for feisty?

Please tell us your partition, ie....hdb or sda, or whatever...
Also, did you make a directory for where you wanna mount it?
if not, just type this:
```
sudo mkdir /media/Backups (or any other name)
```

then....

```
sudo mount /dev/<<Partition>> /media/Backups (or name given above)
```

That should work. 
To mount the internal drive every time, just edit your fstab file.
Help about it here:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by kditty on 2007-04-25
-------sudo fdisk -l-------

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19170   153982993+  83  Linux
/dev/sda2           19171       19452     2265165    5  Extended
/dev/sda5           19171       19452     2265133+  82  Linux swap / Solaris

[B][B][I]Disk /dev/sdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15504   117210208+   7  HPFS/NTFS[/I][/B][/B]

----------

/dev/sdb1 is the drive i need to access. it shows up under  sudo fdisk -l but not under the disk analyzer.

edit: also, im not so sure the drive is  ntfs since i cleared it when i went to dapper as a main OS. its a shame i forgot to back up my old fstab but i remember someone told me that the system label isnt always correct. i read AND write to this drive and have been for almost a year.

---

### Post by marko_4454 on 2007-04-25
I am not sure if your drive is ntfs or not...maybe someone can help, but if it is try this:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+mount](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+mount)

IF it isnt, then just do this:
```
sudo mkdir /media/Backups
```
```
sudo mount /dev/sdb1 /media/Backups
```


edit your etc/fstab file by adding this:
```
/dev/sdb1      /media/Backups    ext3<guessing it is ext3>    defaults     0      2
```

---

### Post by kditty on 2007-04-25
> **marko_4454 said:**
> I am not sure if your drive is ntfs or not...maybe someone can help, but if it is try this:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+mount](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+mount)

IF it isnt, then just do this:
```
sudo mkdir /media/Backups
```
```
sudo mount /dev/sdb1 /media/Backups
```


edit your etc/fstab file by adding this:
```
/dev/sdb1      /media/Backups    ext3<guessing it is ext3>    defaults     0      2
```

thanks, i used this guide [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) i think its pretty much what you told me. thanks everyone

---

