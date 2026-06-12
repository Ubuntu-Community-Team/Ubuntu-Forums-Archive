---
title: "Accessing my external HD"
date: 2006-06-17
forum: Apple PPC Users
---

### Post by maxmartin on 2006-06-17
I kind of already asked about this in another thread, but it had an unrelated title and wasn't getting any new responses, so I thought I'd just start up a sepearate thread for it.

I have a 160 GB NetDisk external HD which contains, among other things, all of my music. Under Disks Manager, device is listed as "dev/sda", and the partitions are of the type Extended 2. As per someone's advice, I edited my /etc/fstab file, and added this line:

```
/dev/sda   /media/hd   ext2   defaults
```

And this is the reaction I get:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Also, if I attempt putting "auto" under file system type, I get this response;

```
mount: you must specify the filesystem type
```

Anybody know how I can mount this HD and access these files? If I can't, it's going to be really impractical to use Ubuntu, since so much of what I use my computer for is managing and listening to music.

---

### Post by tidris on 2006-06-17
I think the problem is you didn't specify which disk partition to mount.
In other words, use /dev/sdaX where X is the partition number you want to mount.
You can try it by hand using the mount command. For example this would  mount partition 2 in the disk:

sudo mount  /dev/sda2  /media/hd

Also note the /media/hd directory must already exist before you try to mount a partition there.

---

### Post by maxmartin on 2006-06-17
Taking your suggestion, I changed it to /dev/sda3 (which is the partition I want), and I get this error when I attempt to mount it:

```
mount: special device /dev/sda3 does not exist
```

---

### Post by tidris on 2006-06-17
[QUOTE=maxmartin]Taking your suggestion, I changed it to /dev/sda3 (which is the partition I want), and I get this error when I attempt to mount it:

```
mount: special device /dev/sda3 does not exist
```[/QUOTE]
What do you get when you type this in a terminal window:

ls /dev/hd*

ls /dev/sd*

sudo fdisk -l

---

### Post by maxmartin on 2006-06-17
```
max@linmax:~$ ls /dev/hd*
/dev/hda   /dev/hda2  /dev/hda4  /dev/hda6
/dev/hda1  /dev/hda3  /dev/hda5  /dev/hdc
max@linmax:~$ ls /dev/sd*
/dev/sda
max@linmax:~$ sudo fdisk -l
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2              Apple_Free                       262144 @ 64        (128.0M)  Free space
/dev/sda3               Apple_HFS Apple_HFS_Untitled_2 312319584 @ 262208    (148.9G)  HFS
/dev/sda4              Apple_Free                           17 @ 312581792 (  8.5k)  Free space

Block size=512, Number of Blocks=312581809
DeviceType=0x0, DeviceId=0x0

/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 97656251  (977.0k)  NewWorld bootblock
/dev/hda3               Apple_HFS Apple_HFS_Untitled_1  97394043 @ 262208    ( 46.4G)  HFS
/dev/hda4         Apple_UNIX_SVR2 untitled            18679688 @ 97658205  (  8.9G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap                  872347 @ 116337893 (426.0M)  Linux swap
/dev/hda6              Apple_Free Extra                 262144 @ 64        (128.0M)  Free space

Block size=512, Number of Blocks=117210240
DeviceType=0x0, DeviceId=0x0


```

---

### Post by tidris on 2006-06-17
Ok, I see a problem right away. The sda3 partition is in hfs or hfsplus format, not ext2. That is definitely part of the problem since you though it was ext2. You need to change fstab so it specifies hfsplus or hfs for that partition.

Another problem I see is that there aren't device files for the partitions in sda. There ought to be sda1 to sda4. I am not sure what to do about that. Perhaps disconnect and reconnect the external disk? 

[EDIT] I just noticed that when I connect my firewire disk to the computer under ubuntu the hfsplus partition in it is automatically mounted for me and a brower window automatically opens. Evidently there is some background process looking for removable disks to appear and automatically mounts them for me.  I didn't do anything special to make that happen, it seems to be the default behavior after installing 6.06.

---

### Post by maxmartin on 2006-06-17
Boo-yah! All I had to do was change the format to hfsplus and the first line to just /dev/sda, and it mounted correctly. Probably should have figured that out myself. Thanks a ton for the pointers!

---

### Post by maxmartin on 2006-06-18
Okay, this is sort of related - using the same procedure, I managed to mount the mac partition of my HD, but I don't have access to any of my user files. Is there any way to get myself access other than making my account public? I mean, I guess there's no reason I can't do that, I was just wondering.

---

### Post by tidris on 2006-06-18
[QUOTE=maxmartin]Okay, this is sort of related - using the same procedure, I managed to mount the mac partition of my HD, but I don't have access to any of my user files. Is there any way to get myself access other than making my account public? I mean, I guess there's no reason I can't do that, I was just wondering.[/QUOTE]
You can try this if using GNOME: 

```
sudo nautilus
```

I am sure there is something equivalent for KDE but I don't know what it is.

---

### Post by maxmartin on 2006-06-18
Sweet. Okay, one more question - if I want to safely eject my hard drive, what do I do? Is there just an unmount command or something?

---

### Post by maxmartin on 2006-06-18
Okay, awesome. Of course, now I have another - it seems to have mounted my HD as a read-only file system. What can I do about that?

---

### Post by tidris on 2006-06-18
[QUOTE=maxmartin]Okay, awesome. Of course, now I have another - it seems to have mounted my HD as a read-only file system. What can I do about that?[/QUOTE]
That seems to happen if the hfsplus partition is journaled. You could turn journaling off with the OSX diskutil command. I don't know if there is a linux command that could do the same.

---

### Post by tidris on 2006-06-18
[QUOTE=maxmartin]Sweet. Okay, one more question - if I want to safely eject my hard drive, what do I do? Is there just an unmount command or something?[/QUOTE]
There is the umount command. If the partition is mounted at /media/hd, you would use
```
 sudo umount /media/hd
```

There is also a linux eject command I just learned about. See man eject.

---

### Post by maxmartin on 2006-06-18
Sweet, thanks a ton for the help.

---

