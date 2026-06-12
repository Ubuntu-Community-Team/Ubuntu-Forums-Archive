---
title: "[SOLVED] Network drive read/write help"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by zamael on 2008-02-12
so here's what I got going... I'm sure it's something simple as I am really new to Ubuntu...

sudo fdisk -l:
```
Disk /dev/hda: 46.1 GB, 46115758080 bytes
255 heads, 63 sectors/track, 5606 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc28dc28

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5371    43142526   83  Linux
/dev/hda2            5372        5606     1887637+   5  Extended
/dev/hda5            5372        5606     1887606   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0de10de0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

```

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e8ee6dd9-021b-46fc-ba69-c13adb881478 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c97e9dd7-2ed4-4b68-87b6-d4d556149b43 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
[COLOR="Red"]//cjroberts/backup  /media/cjroberts/backup  smbfs credentials=~/.smbcredentials 0 0
//cjroberts/downloads  /media/cjroberts/downloads smbfs rw,user,credentials=~/.smbcredentials 0 0
//cjroberts/share  /media/cjroberts/share  smbfs rw,user,credentials=~/.smbcredentials 0 0[/COLOR]
/dev/sda1 /media/sda ntfs-3g defaults,nls=utf8,umask222 0 0
```

The drives I cannot seem to get right are the three located on //cjroberts.  I can view everything and it mounts but I cannot write/delete any files.  If I go to Go > Network and attempt to connect through the network I _can_ write/delete files.  

I searched the forums here numerous times and tried just about everything I have found.  When I do a ```
sudo nautilus
``` and attempt to change the rights on the folders in my /media folder it won't seem to work.  I change it to read/write and it takes for 2 seconds then changes back to Read Only by itself.  

So any thoughts what I might have screwed up?  Thanks for everyone's help!

---

### Post by hyper_ch on 2008-02-12
I guess the issue is this:

```

~/.smbcredentials

```

Upon booting that would be root user. So the folder you give there would be
```

/root/.smbcredentials

```
Which I doubt it is.

I assume you use ~/.smbcredentials for your own user, so it would be something like
```

/home/zamael/.smbcredentials

```

Just give full path there and I guess it will work (never done that myself actually)

---

### Post by oedha on 2008-02-12
i had this problem.......sometimes ago
first : make sure that the shared folders have the correct mode (rwx)
sudo chmod 777 /shared
and i suggest you to use cifs instead of smbfs

---

### Post by zamael on 2008-02-12
okay... so I double checked everything and the network drives are completely open... no user or password is required to log into them.  Tested by going to Go > Network > cjroberts and being able to create/delete files, folders, etc.  

I changed the fstab to read:
```
//cjroberts/backup  /media/cjroberts/backup  cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//cjroberts/downloads  /media/cjroberts/downloads cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//cjroberts/share  /media/cjroberts/share  cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

still no luck... now I can't even get the drives to mount!  What am I doing wrong?

---

### Post by _sAm_ on 2008-02-12
What happens if you try to mount the share directly without going to /etc/fstab ?

---

### Post by hyper_ch on 2008-02-12
```

//cjroberts/backup  /media/cjroberts/backu smbfs credentials=/home/zamael/.smbcredentials,uid=1000,gid=1000 0 0

```

How does this work?

---

### Post by zamael on 2008-02-12
> **_sAm_ said:**
> What happens if you try to mount the share directly without going to /etc/fstab ?

If I go to file browser and then Go > Network > CJRoberts and I can access it with no problem and have all rights (read/write)...

---

### Post by zamael on 2008-02-12
> **hyper_ch said:**
> ```

//cjroberts/backup  /media/cjroberts/backu smbfs credentials=/home/zamael/.smbcredentials,uid=1000,gid=1000 0 0

```

How does this work?

Says: "ERROR: Unable to open credentials file!"

---

### Post by zamael on 2008-02-12
> **hyper_ch said:**
> ```

//cjroberts/backup  /media/cjroberts/backu smbfs credentials=/home/zamael/.smbcredentials,uid=1000,gid=1000 0 0

```

How does this work?

I screwed up the line... after fixing it and attempting it again it worked!  Thanks hyper_ch!!!!!!

here are the lines that worked for me in case someone has the same scenario:
```
//cjroberts/backup  /media/cjroberts/backup  smbfs credentials=/home/john/.smbcredentials,uid=1000,gid=1000 0 0
//cjroberts/downloads  /media/cjroberts/downloads smbfs credentials=/home/john/.smbcredentials,uid=1000,gid=1000 0 0
//cjroberts/share  /media/cjroberts/share  smbfs credentials=/home/john/.smbcredentials,uid=1000,gid=1000 0 0
```

---

### Post by hyper_ch on 2008-02-13
well, I didn't know where you had your credentials saved ;)

---

