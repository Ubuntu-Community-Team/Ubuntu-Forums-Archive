---
title: "I read a lot, but still have problems, please help!!!"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by paripamano on 2006-11-13
sadly I'm an absolute beginner in linux and ubuntu.
Right now i have some mounting problems.

I have two hard drives: the first one (80Gb) is where my windows xp and linux is. There are three partitions hda1 - win xp, hda2 - called extended, but gparted shows it has three "partitions" "in it". the swap, the linux and one fat32. 

The second one is where I have no OS, only video files for my work. it's ntfs 160 Gb sda, no partitions (I mean one).

I had trouble mounting the Fat32 partition on my 80 Gb drive (where my music is), becasue so many methods, and problems, but it seems to be OK now. 

I tried: gksudo gedit /etc/pmount.allow
and other two methods, I hope I didn't spoil anything, because trying a lot of methods. I didn't even know how many space to leave between things in fstab. anyway.

But the 160 Gb sda I can't reach (it's not where i mounted) although the fstab shows this (and gparted tells it is mounted to /media/share:

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=c32dcb73-1069-4566-906e-b090ecd4d408 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=4efd8742-1d70-4716-9338-69ffb7b09a4e none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /media/share ntfs umask=0222 0 0
/dev/hda5 /media/share vfat umask=0222 0 0


This is my fdisk -l:


Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        5848    31615920    f  W95 Ext'd (LBA)
/dev/hda3            5849        9733    31206262+  83  Linux
/dev/hda5            1913        5679    30258396    b  W95 FAT32
/dev/hda6            5680        5848     1357461   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   42  SFS



Strange thing, when i want to edit fstab: (is it normal?):

paripamano@paripamano-desktop:~$ gksudo gedit /etc/fstab

(gedit:6366): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I hope somebeody understands what i was writing here. I don't understand a lot of things, that's why it is probably a mess.

thank you a lot for any help:) 

almost forgot: in /dev there was sda, sda1, sda2 , but now there is only sda. I didn't understand it earlier either, because it's a one partition drive, but now, i even don't understand the change. probably i did mess things up.:(

---

### Post by roger99 on 2006-11-13
It looks to me like you are trying to mount two seperate partitions in the same directory, /media/share

Try editing your fstab using this command

```
sudo gedit /etc/fstab
```

edit this line
```

/dev/sda1 /media/share ntfs umask=0222 0 0
```

So that it looks more like this

```
/dev/sda1 /media/share ntfs defaults,nls=utf8,umask=007   0       1
```

The second line in your fstab that is causing you problems is this

```
/dev/hda5 /media/share vfat umask=0222 0 0
```

This is where you are mounting another fat32 partition in the same place as the previous NTFS partition.

Create another directory in media called, for example, share2.
```

sudo mkdir /media/share2
```

Then editing your fstab again change the line concerning hda5 to something like

```
/dev/hda5 /media/share2  vfat defaults,utf8,umask=007   0       1
```

Once you have done this issue this command in a terminal and, hopefully, all should be well

```
sudo mount -a
```

---

### Post by steve.horsley on 2006-11-13
There are two things I don't understand here.

1) Your fdisk listing for hda doesn't show an extended partition. My fdisk does. I don't understand why. But that's not the big problem.

2) fidsk says the partition on your hdb is of type SFS (id 42). I have never heard of this type of partition. Do you know what filesystem type is on it?

Edit:
And I missed what roger99 spotted - youare trying to mount two partitions on the same mount point.

---

### Post by paripamano on 2006-11-13
well I tried what you wrote down. now my 80 Gb mounted partition is gone.  it was there, with all my music, now it isn't and i have a /share dir with no permission to access. sda1 still didn't mount. terminal says no such device found.

Gparted shows:

/dev/hda1 -ntfs
/dev/hda2 -extended
      /dev/hda5 fat32     
      /dev/hda6 linux swap
/dev/hda3 -ext3

---

### Post by roger99 on 2006-11-13
> 2) fidsk says the partition on your hdb is of type SFS (id 42). I have never heard of this type of partition. Do you know what filesystem type is on it?

Steve is right, i didn't spot this.  A quick google looks like this is some form of encrypted filesystem.  My fstab entry for this disk might not therefore work.

You may have to do some more research here, i'll have a read and try and get back to you on it.

---

### Post by paripamano on 2006-11-13
gparted shows sda is an ntfs file, i can see fdisk shows it's some kind of SFS. i don't understand.

i have no hdb though. only hda and sda.

---

### Post by roger99 on 2006-11-13
First for the permissions problem, i forgot to include the gid parameter on the fstab line.

Without it both the partitions would have root only access

Should have looked more like
```

/dev/hda5 /media/share2  vfat defaults,utf8,umask=007,gid=046   0       1
```

Try adding this parameter to both the fstab lines and see what happens!:-D

EDIT: to make sure this is the right gid number for you in a terminal enter

```
cat /etc/group
```

and have a look to see which group id your user has been given

---

### Post by paripamano on 2006-11-13
what i got to: cat /etc/group is a lot of stuff i don't understand, but no gid found.

i tried to do back, the fat32 partition mounting the way it was:

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=c32dcb73-1069-4566-906e-b090ecd4d408 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=4efd8742-1d70-4716-9338-69ffb7b09a4e none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /media/mnt ntfs defaults,nls=utf8,umask=007   0       1
/dev/hda5 /media/share vfat umask=0222 0 0


, and now i can see it. i hope i can write to it. but the other drive sda which i mounted to a dir /media/mnt is still empty. when i type:

 sudo mount -a

it says no special device.

---

### Post by roger99 on 2006-11-13
It would appear that your disk (sda) uses windows dynamic disks.  A form of partitioning used for applications such as servers/RAID arrays.  The partition info is held in a database in the last 1MB of the disk.  As far as I can assertain linux doesn't support it as standard and requires LDM support to be complied into the kernel.  This is about as far as my searching has got me as I keep getting old info.  More research needed i think ](*,)
> 
Dynamic Disk
A Win2K dynamic disk is a physical disk that doesn't use partitions or logical drives. Instead, it contains only dynamic volumes that you create in the Disk Management console. Regardless of what format you use for the file system, only Win2K computers can access dynamic volumes directly. However, computers that aren't running Win2K can access the dynamic volumes remotely when connected to the shared folders over the network. In NT, what we call sets (e.g., mirrored sets, striped sets) are in Win2K called volumes (e.g., mirrored volumes, striped volumes). . . .

Errr.......

---

### Post by paripamano on 2006-11-14
sorry for not replying, but went sleeping last night. 

-do you think it is better to delete my video files, make a fat32 partition of the sda with gparted, or just dont use it in ubuntu, only in xp. actually i edit my videos in adobe premiere in xp. 
or i cannot use this drive in whatever format it is (fat32, ntfs etc.). i don't understand why though. it's a new samsung drive HD 160JJ. Gparted shows a strangely that this drive is almost full, but the truth is, that it is almost empty right now. Why is it showing this? totally wierd.

-can i make a fat32 out of the drive without deleting files?

-is it ok to leave hda5 mount like this in fstab (like this i can read it):

/dev/hda5 /media/share vfat umask=0222 0 0

-am i able to write in it?

thanx for the answers!

---

### Post by roger99 on 2006-11-14
Hello again, I slept after my last post so no need to apologise for that. ;) 

After all my searching last night it turns out that in this forum people have been able to access SFS disks in ubuntu.  Although that was probably read only anyway like NTFS.  There is a way to convert SFS dynamic disks back to standard NTFS basic disks although this sounds a little risky.

[http://thelazyadmin.net/index.php?/archives/161-Converting-Dynamic-Disks-Back-to-Basic-Disks.html](http://thelazyadmin.net/index.php?/archives/161-Converting-Dynamic-Disks-Back-to-Basic-Disks.html)

If you want to be able to read & write to your disk in ubuntu, it may be a good option to backup all your data in XP and use gparted to wipe the disk, start again and create a FAT32 partition and put everything back onto it.  This way you would have read and write access in both XP and linux.  Unfortunatly there is no way to convert this disk to FAT32 without losing all your data.

As for leaving hda5 mounted like this that is not a problem but you should be able to have this disk as readable and writable.  It's just gonna take some fiddling with the options in fstab to make it so.  I'll get back to you on that :???:

EDIT: Can you let me know your ubuntu username and the output of "cat /etc/group" so I can help a little more with permissions of hda5

---

