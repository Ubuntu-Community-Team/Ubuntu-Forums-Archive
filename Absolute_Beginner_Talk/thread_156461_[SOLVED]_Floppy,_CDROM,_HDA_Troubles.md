---
title: "[SOLVED] Floppy, CDROM, HDA Troubles"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Goldpin on 2006-04-07
I just reinstalled Breezy.  When I first installed it, my HDA showed up on the desktop, but said I couldn't access it because I didn't have the necessary permissions and there were no icons for my floppy or CDROM drives.

Now none of them appear on my desktop and I can't access them at all.

I'm using a dual boot system with windows on HDA which is formatted as NTFS.  Ubuntu is on HDB.  I've tried modprobe to find both the floppy and HDA, but nothing happened.  The CDROM and floppy appear in places, but not HDA.

Help please.

---

### Post by localzuk on 2006-04-07
Hi, could you post the contents of your /etc/fstab file here please?

---

### Post by Sutekh on 2006-04-07
The fstab will tell us how Ubuntu is attempting to mount the partitions (if at all), so it would also be useful to know a little more about them, where they are and what format
```
sudo fdisk -l
```will list all your partitions with details

---

### Post by Goldpin on 2006-04-12
[QUOTE=localzuk]Hi, could you post the contents of your /etc/fstab file here please?[/QUOTE]

/etc/fstab is as follows:

<file system> <mount point>   <type>  <options>   <dump>  <pass>
proc             /proc                proc      defaults     0           0
/dev/hdb1     /                      ext3      defaults,errors-remount-ro 0   1
/dev/hdb5     none                 swap     sw            0           0      
/dev/hdc       /media/cdrom0   udf,iso9660 user,noauto  0     0
/dev/fd0       /media/floppy0    auto      rw,user,noauto  0    0

I have added a line for hda1.  However in the "system" disk manager hda is shown and the mount point is /media/hda (I think) but it's shown as inaccessable and the button to activate it doesn't work.

My grub bootloader is on hda and I think it might be partitioned from the rest of the drive.  Could this have something to do with hda being unaccessable?

hda is formatted as NTFS.  I know I can't write to it, but would like to have the files accessable for copying into ubuntu.

---

### Post by Sef on 2006-04-12
> hda is formatted as NTFS. I know I can't write to it, but would like to have the files accessable for copying into ubuntu.

To share files, you need to have a partition that is either FAT32 or ext2.

---

### Post by Goldpin on 2006-04-12
[QUOTE=Sef]To share files, you need to have a partition that is either FAT32 or ext2.[/QUOTE]

Does that mean all of hda needs to be formatted as FAT32 or can I just partition part of it and then be able to access the NTFS portion as well?

---

### Post by Sutekh on 2006-04-12
[QUOTE=Goldpin]

hda is formatted as NTFS.  I know I can't write to it, but would like to have the files accessable for copying into ubuntu.[/QUOTE]

If the NTFS drive is /dev/hda1 (you can confirm with sudo fdisk -l) then add this line to your /etc/fstab
```
/dev/hda1   /windows   ntfs   nls=utf8,umask=0222   0   0
```
You will need to create the mount folder (in this case /windows, but it can be whatever you like) with
```
sudo mkdir /windows
```
Then use
```
sudo mount -a
``` to remount your partitions including the Windows one.

As you know you can't write to it, but you will be able to access it.

---

### Post by Princey on 2006-04-12
[QUOTE=Sutekh]If the NTFS drive is /dev/hda1 (you can confirm with sudo fdisk -l) then add this line to your /etc/fstab
```
/dev/hda1   /windows   ntfs   nls=utf8,umask=0222   0   0
```
You will need to create the mount folder (in this case /windows, but it can be whatever you like) with
```
sudo mkdir /windows
```
Then use
```
sudo mount -a
``` to remount your partitions including the Windows one.

As you know you can't write to it, but you will be able to access it.[/QUOTE]


In addition to what sutketh just said, he might still have trouble mounting the drive unless he tells the system to release it. Safest bet after he follows your prompt is to remove the extra line > /dev/hda1 and before issuing > mount -a he issues the command > sudo umount to free up root holding on to dev/hda1. I've seen persons post about the aforementioned. With your directions, he'll have to make a link or shortcut on the desktop to link to /windows in his home directory and change the icon to that of a 'drive' if he wants that effect.

---

### Post by Squiddish on 2006-04-15
Good morning all.

I'm having some issues mounting some of my partitions and my cdrom as well.

I'm a linux n00b, and I'm running breezy 5.10.  I've got some additional partitions on my disk that I've formatted as fat32 so that I can read/write back and forth between windows and ubuntu.

I created them using Partition Magic under windows, and when I restarted, I can't mount either them or my cdrom (which was mounting fine before I created the new partitions)

Anyway, here is my fstab:
```
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda1 /media/hda1 ntfs defaults,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
/dev/hda6 /media/hda6 ext2 ,atime,auto,rw,nodev,exec,nosuid,users 0 0
/dev/hda7 /media/hda7 ext2 ,atime,auto,rw,nodev,exec,nosuid,users 0 0
/dev/hdc /media/hdc ext2 ,atime,noauto,ro,nodev,noexec,nosuid,nouser 0 0

```

and here is the output of an fdisk -l
```

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    7  HPFS/NTFS
/dev/hda2             638        1610     7815622+  83  Linux
/dev/hda3            1611       24321   182426107+   f  W95 Ext'd (LBA)
/dev/hda5            1611        1853     1951866   82  Linux swap / Solaris
/dev/hda6            1854       11573    78075868+   b  W95 FAT32
/dev/hda7           11574       24321   102398278+   b  W95 FAT32

```
and this is what happens when I run mount -a
```

mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda7,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Any help would be appreciated :)

---

### Post by Squiddish on 2006-04-15
As an update, I managed to get the FAT32 partitions properly defined, but I'm not sure how to get them to show up in my storage media area (I'm running KDE).
Still no luck getting my CD ROM to mount =/

---

### Post by Princey on 2006-04-15
[QUOTE=Squiddish]As an update, I managed to get the FAT32 partitions properly defined, but I'm not sure how to get them to show up in my storage media area (I'm running KDE).
Still no luck getting my CD ROM to mount =/[/QUOTE]

Here's what to do. Change the following lines > /dev/hda6 /media/hda6 ext2 ,atime,auto,rw,nodev,exec,nosuid,users 0 0
/dev/hda7 /media/hda7 ext2 ,atime,auto,rw,nodev,exec,nosuid,users 0 0 to read > /dev/hda6 /media/hda6 vfat auto,rw,user 0 0
/dev/hda7 /media/hda7 vfat auto,rw,user 0 0

Then type > sudo umount followed by > sudo mount -a

Let me know if you still have problems.

---

### Post by Sutekh on 2006-04-15
[QUOTE=Squiddish]As an update, I managed to get the FAT32 partitions properly defined, but I'm not sure how to get them to show up in my storage media area (I'm running KDE).
Still no luck getting my CD ROM to mount =/[/QUOTE]
The line in your fstab for your CDROM is currently
```
/dev/hdc /media/hdc ext2 ,atime,noauto,ro,nodev,noexec,nosuid,nouser 0 0
```
You need to change it to this one
```
/dev/hdc   /media/cdrom0   udf,iso9660   ro,user,noauto   0   0
```

---

### Post by Squiddish on 2006-04-16
Well I've made all of the changes as instructed, and nothing mounts :/
When I try to insert a CD into the drive, I get:
```

An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist.

```

Also, if I do a fdisk -l as my user, it returns nothing.
When I use sudo to run the command, I get:
```

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    7  HPFS/NTFS
/dev/hda2             638        1610     7815622+  83  Linux
/dev/hda3            1611       24321   182426107+   f  W95 Ext'd (LBA)
/dev/hda5            1611        1853     1951866   82  Linux swap / Solaris
/dev/hda6            1854       11573    78075868+   b  W95 FAT32
/dev/hda7           11574       24321   102398278+   b  W95 FAT32

```

This lead me to believe that maybe I would see them if I logged in as root, so I enabled the root login and tried it. Still nothing :/

It's just bizarre because when I go into system -> settings -> disk and media I can see everything as being enabled.

Oh yeah I almost forgot, here is my new fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda1 /media/windows ntfs ,uid=0,gid=0,auto,rw,user 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
/dev/hda6 /media/Apps vfat ,uid=0,gid=0,auto,rw,user 0 0
/dev/hda7 /media/data vfat ,uid=0,gid=0,auto,rw,user 0 0

/dev/hdc /media/cdrom0 iso9660 noauto 0 0

```

I don't understand why the hdc is in there twice, as I pulled out the second one when I did the edit.

---

### Post by Princey on 2006-04-16
[QUOTE=Squiddish]Well I've made all of the changes as instructed, and nothing mounts :/
When I try to insert a CD into the drive, I get:
```

An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist.

```

Also, if I do a fdisk -l as my user, it returns nothing.
When I use sudo to run the command, I get:
```

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    7  HPFS/NTFS
/dev/hda2             638        1610     7815622+  83  Linux
/dev/hda3            1611       24321   182426107+   f  W95 Ext'd (LBA)
/dev/hda5            1611        1853     1951866   82  Linux swap / Solaris
/dev/hda6            1854       11573    78075868+   b  W95 FAT32
/dev/hda7           11574       24321   102398278+   b  W95 FAT32

```

This lead me to believe that maybe I would see them if I logged in as root, so I enabled the root login and tried it. Still nothing :/

It's just bizarre because when I go into system -> settings -> disk and media I can see everything as being enabled.

Oh yeah I almost forgot, here is my new fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda1 /media/windows ntfs ,uid=0,gid=0,auto,rw,user 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
/dev/hda6 /media/Apps vfat ,uid=0,gid=0,auto,rw,user 0 0
/dev/hda7 /media/data vfat ,uid=0,gid=0,auto,rw,user 0 0

/dev/hdc /media/cdrom0 iso9660 noauto 0 0

```

I don't understand why the hdc is in there twice, as I pulled out the second one when I did the edit.[/QUOTE]


I think the reason why you aren't able to access the FAT partitions is because the directories doesn't exist. You already have the FAT partition entries in your fstab so let's get them fixed. Open the terminal and type the following: > sudo mkdir /media/Apps followed by > sudo mkdir /media/data.

I'm not too sure for the CDROM but here's my fstab line for my CDROM Drive > /dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Try that and see. Enter > sudo mount -a when done. This should work. Let me know if it doesn't.

---

### Post by Squiddish on 2006-04-16
Ok, I restarted under the recovery mode and ran startx from the command prompt.

This drops me into KDE as root (I think) and like magic, everything is mounted and I can access everything.  But when I restart and log in as usual, poof they're gone.

I've checked the directories in the media directory and they are there and named properly :/

---

### Post by Princey on 2006-04-16
[QUOTE=Squiddish]Ok, I restarted under the recovery mode and ran startx from the command prompt.

This drops me into KDE as root (I think) and like magic, everything is mounted and I can access everything.  But when I restart and log in as usual, poof they're gone.

I've checked the directories in the media directory and they are there and named properly :/[/QUOTE]


Did you try what I asked you to try?

---

### Post by Squiddish on 2006-04-16
[QUOTE=Princey]Did you try what I asked you to try?[/QUOTE]

Yeah, no dice.  I can only see the cdrom and partitions when logged into KDE from the recovery console.  

If, however, I go to the media directories where the partions are supposed to be mounted to, I can access them there.

---

