---
title: "Gateway mp3 player not recognized"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-07
I have a usb stick that seems to work ok, but i plug in my usb mp3player and no luck. It should work as a standard drag and drop, which is why I like it. How might I go about mounting this thing?

---

### Post by Inxsible on 2007-06-07
could you post the output of```
df -h 
gedit /etc/fstab
```

---

### Post by Inxsible on 2007-06-07
Make sure your mp3 player is connected when you do that

---

### Post by FleetAdmiral74 on 2007-06-07
First command got:
ed@ed-desktop:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              92G   15G   73G  18% /
varrun                379M  116K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  108K  379M   1% /proc/bus/usb
udev                  379M  108K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1              77G   27G   51G  35% /media/hda1
ed@ed-desktop:~$ 

Second got 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=401ddaee-0801-4727-9c47-4f925be646ec /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=D0A8A1A1A8A18696 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=076b4cdc-67bf-4900-a4fd-1815e68e4150 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

btw, how to I put this in that code windows so its smaller when I post?

---

### Post by Inxsible on 2007-06-07
> **FleetAdmiral74 said:**
> 
btw, how to I put this in that code windows so its smaller when I post?

you use [ code ] and [/code ] around the text you want in the box without spaces

---

### Post by Inxsible on 2007-06-07
can you also post the output of ```
sudo fdisk -l
```

---

### Post by FleetAdmiral74 on 2007-06-07
here it is
```
ed@ed-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       12158    97659103+  83  Linux
/dev/hdb2           12159       12220      498015   82  Linux swap / Solaris
/dev/hdb3           12221       30401   146038882+   5  Extended
ed@ed-desktop:~$ 

```

edit: dont see it there, its 128mb just fyi

---

### Post by Inxsible on 2007-06-07
> **FleetAdmiral74 said:**
> here it is


edit: dont see it there, its 128mb just fyi

was your mp3 player connected when you did this ?

---

### Post by FleetAdmiral74 on 2007-06-07
Yep, the light on it goes on so I know its actually getting power.

---

### Post by Inxsible on 2007-06-07
Cant really say much about mounting it, if it doesnt show up in fdisk. Does it need some specialized drivers or something?

---

### Post by FleetAdmiral74 on 2007-06-07
I do not believe it needs special anything, just drag and drop functionality. I will retry above steps in case I missed something...

edit: well after the first command, i got a line that just said "ile"....no other numbers or anything...idk what that was about
double edit: well, going to bed. Will check up on this in the morning, thanks for sticking with it so far.

---

### Post by FleetAdmiral74 on 2007-06-07
```
$ sudo bump
```

---

### Post by FleetAdmiral74 on 2007-06-25
grr...nother bump!

---

