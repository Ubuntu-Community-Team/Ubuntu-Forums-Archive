---
title: "XP Disk access?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Danondorf on 2007-12-19
Hey, I was wondering if there was any way to access data from a disk I'm using exclusively for xp. I'd like to be able to access my media files without having to copy them to my ubuntu disk. thanks

---

### Post by KhaaL on 2007-12-19
It should work automatically.  could you post the contents of your /etc/fstab ?
(just run gedit, open /etc/fstab and paste it).

---

### Post by hyper_ch on 2007-12-19
there are multiple ways to do it.

You could make use of a seperate fat32 partition or you could use ntfs-3g

---

### Post by Danondorf on 2007-12-20
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1091f994-f3e0-4102-b852-8055536ec317 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=539769c0-dc35-4372-ae32-22ed02dc997d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by nick_h on 2007-12-20
You will need to create a mount point for your Windows partition.  Then you can add an entry in fstab similar to:
```
/dev/sda1    /media/Windows    ntfs-3g    defaults,umask=007,gid=46    0    1
```

---

### Post by Danondorf on 2007-12-25
I now have a blank /media/windows/ folder, is ntfs-3g working right?

---

### Post by lgambett on 2007-12-25
You should;
1) modify /etc/fstab following the instruction of the previous post
2) issue the command
*sudo mount -a*
or reboot in order to activate the new mounting table.
Pay also attention to capital letters (windows and Windows are different)

---

### Post by nick_h on 2007-12-25
What version of Ubuntu you are using?

If you are running Gutsy use ntfs rather than ntfs-3g (Gutsy has write support for ntfs by default).

If you are running Feisty or earlier you will need to install the ntfs-3g package first.

---

### Post by Danondorf on 2007-12-26
I'm running 7.10, so I should be able to use ntfs.
I tried switching that line from ntfs-3g to ntfs and it now works when I use 'sudo mount -a' but that just mounts it like a cd or floppy drive, I've been talking to some other gutsy users who say they have windows disk access automatically. Does anyone have any ideas why I wouldn't already be able to read and write to my xp disk?

---

### Post by nick_h on 2007-12-26
It should mount automatically on each boot now.  You should also have read/write access.  When you say that it "just mounts it like a cd or floppy drive" do you mean that it doesn't mount at boot time?

It is possible that for some reason the device is not available when the system tries to mount it.  In this case you would expect some errors in your log files.  Start by looking at the output from dmesg.

```
dmesg | less
```

---

### Post by jflarm on 2007-12-26
In a prior responce nick_h appointed this line for the /etc/fstab:

/dev/sda1    /media/Windows    ntfs-3g    defaults,umask=007,gid=46    0    1

You only need to change the mount options:
defaults,users,umask=007	0	0

The gid=46 option sets the group id to 46, which is the plugdev group. Since this is not a pluggable device I think you should be fine without it.
The last 1 changed to a 0 means that the system won't check the partition upon reboot.

This is the line you need:
/dev/sda1    /media/Windows    ntfs-3g    defaults,users,umask=007	0	0

---

