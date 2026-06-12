---
title: "Unmounting a partition"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by mpkiche on 2007-05-30
When I installed Ubuntu I set up two new partitions, one for root one for home, which went fine. However it automatically mounts my windows partition on startup as well and sticks an icon for it on the desktop. 

How do I stop it mounting the partition on startup or how can I just remove the hard disk icon from the desktop?

Cheers
Matt

---

### Post by Inxsible on 2007-05-30
> **mpkiche said:**
> When I installed Ubuntu I set up two new partitions, one for root one for home, which went fine. However it automatically mounts my windows partition on startup as well and sticks an icon for it on the desktop. 
 
How do I stop it mounting the partition on startup or how can I just remove the hard disk icon from the desktop?
 
Cheers
Matt
 
You would have to edit your /etc/fstab file
```
gksudo gedit /etc/fstab
```
 
copy paste its contents and we can help you out more

---

### Post by daimaru on 2007-05-30
if you dont want it to mount at all edit your /etc/fstab file
```
sudo gedit /etc/fstab
```

comment out your windows partition it should have ntfs in there somewhere for example:
/dev/hda1   /media/hda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
change to 
#/dev/hda1   /media/hda1   ntfs-3g  defaults,locale=en_US.utf8    0    0

# comments it out so you can get it back if you want.

---

### Post by annda on 2007-05-30
to remove disk/partitions icons from desktop:

```
gconf-editor
```

go to apps>nautilus>desktop and uncheck volumes_visible

to stop the win partition being mounted on boot, comment out its entry in fstab:

```
sudo gedit /etc/fstab
```

put # in front of the line, save the file.

---

### Post by mpkiche on 2007-05-30
Hmmm

Looks like sda2 is already commented out:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cee41f99-9e5f-4b00-afa5-c3756589a308 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=6370ad1d-47c1-4613-a092-3a53fd195ee2 /home           ext3    defaults        0       2
# /dev/sda2
UUID=54CCF353CCF32E3C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=38356d90-1517-4cc4-ac06-fb02d64c52fa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


Any further suggestions??

Thanks guys

Matt

---

### Post by Inxsible on 2007-05-30
No its not commented out. Just below the entry for /dev/sda2, there is a UUID line correct?
 
Comment that out. UUID is another way of identifying your disks

---

### Post by annda on 2007-05-30
hi!

no, only the device name is commented out. the actual entry is in the next line and it uses the UUID insted of the device file name. you need to comment that out too:

# /dev/sda2
**#** UUID=54CCF353CCF32E3C /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

---

### Post by Inxsible on 2007-05-30
Or the better thing to do would be to erase the /media/sda2 in the same line. That is your mount point. Leave the rest as is and your drive will NOT be auto-mounted and of course no icons on the desktop.
 
You can go for either option  :)

---

### Post by mpkiche on 2007-05-30
Jobs a goodun.

Thanks.

---

### Post by lizzie2 on 2007-09-20
Hi from newbie.
Just wanted to say thank you all very much.
Have been trying for ages to remove windows from desk top, plenty of info on mounting them but not on removing.
Worked a treat, also helps us gain confidence in using the command line.
It was a silly thing but annoying to have 3 windows partitions on the clean lines of ubuntu.
Now for the next problem!
Again thank you.
Have fun,
Les

---

