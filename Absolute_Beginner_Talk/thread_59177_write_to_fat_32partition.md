---
title: "write to fat 32partition"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by johnkabuto on 2005-08-23
hi,
sorry to post about this. im sure this will have been addressed before, but i cant find any info.

i mounted my FAT32 partition. Now I can read it OK. but I cant write to it. error message says im not the owner (root is the owner).  how do i change the permissions?

Thanks!
john

---

### Post by aysiu on 2005-08-23
Follow these directions:

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by johnkabuto on 2005-08-23
thank you.
i followed the unofficial ubuntu starter directions originally, and just rechecked now but i still cant write to the fat32 partition.

is there a problem with my fstab entries? (below)

winXP is on hda1 
i want to read/ write to hda6 (fat32: so both winxp and linux can use it)

cheers

---------

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda6       /media/mystuff  vfat    iocharset=utf8,umask=000   0       0

----------

---

### Post by aysiu on 2005-08-23
[QUOTE=johnkabuto]thank you.
i followed the unofficial ubuntu starter directions originally, and just rechecked now but i still cant write to the fat32 partition.

is there a problem with my fstab entries? (below)

winXP is on hda1 
i want to read/ write to hda6 (fat32: so both winxp and linux can use it)

cheers

---------

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda6       /media/mystuff  vfat    iocharset=utf8,umask=000   0       0

----------[/QUOTE] Maybe this is a dumb question, but did you try restarting your computer?

---

### Post by johnkabuto on 2005-08-23
yes rebooted. no change.

i also tried opening a file browser as root, found the partition, right clicked for properties, but it wouldnt let me change the permissions from there either.

---

### Post by xmastree on 2005-08-23
[QUOTE=johnkabuto]/dev/hda6       /media/mystuff  vfat    iocharset=utf8,umask=000   0       0[/QUOTE]
FWIW, my fstab has this:
```
/dev/hdb3	/mnt/shared	vfat	umask=0000	0	0
```
for my shared Fat32 partition.

---

### Post by aysiu on 2005-08-23
[QUOTE=johnkabuto]yes rebooted. no change.

i also tried opening a file browser as root, found the partition, right clicked for properties, but it wouldnt let me change the permissions from there either.[/QUOTE] I'm stumped.

---

### Post by bionnaki on 2005-08-23
you need to change permissions.

sudo
chmod 775 /media/mystuff

---

### Post by johnkabuto on 2005-08-25
thank you for your help.

i tried:
sudo
chmod 775 /media/mystuff

there was no error message after entering the command in terminal, but when i tried to write to the partition, i got the same error message saying i dont have permission to write.

i tried changing my fstab line to:

/dev/hda6	/media/mystuff	vfat	umask=0000	0	0

that seems to have worked.
i'm currently reading/ writing ok in the top level of the fat32 partition. (great!  :smile: )

there are subdirectories in the fat partition that i can not write to (same no permission message)

how can i make these read/ write -able?

thanks
john

---

### Post by nad on 2005-08-25
Use the line: /dev/hda6 /media/mystuff vfat rw,user,auto 0 0  for your filesystem description and mount options (the 0 0 indicate whether the file system should be checked at boot time and in what order). Use the umask option if you need to adjust permissions.

---

### Post by manicka on 2005-08-25
I mount my fat32 drives with an fstab entry  like this and read/write at all levels without problems.

/dev/hda8      /mnt/win_d    vfat    rw,users,gid=users,umask=000, 0 0

---

### Post by johnkabuto on 2005-08-26
problem appears fixed!

thanks all for your help. 

im a bit confused about this issue, but no problem if the fix continues to work! :)  :) 

i followed the change fstab advice: 

/dev/hda6 /media/mystuff vfat rw,user,auto 0 0

but i still got the 'you dont have permission' message when i tried to write.

then i did:

/dev/hda8 /mnt/win_d vfat rw,users,gid=users,umask=000, 0 0

as advised by manicka (thanks) but also still got 'you dont have permission' message.

i plugged in a usb hard drive, which has 3 fat32 partitions, to see what it did. i could read all of them, but only write in 1 of them. the directories and sub directories i created in windowsxp have been allocated various different permissions/ owners, but i cant see an obvious reason for this. i created them all as the same user in windows.
that has confused me!

my fstab is currently:

/dev/hda8 /mnt/win_d vfat rw,users,gid=users,umask=000, 0 0

(slightly in desperation!) i tried again to change permissions manually from a root user file browser (tried before and it didnt work). however, this time is worked, so i have changed the write permissions for the directories i need to write to. 

anyways,

it seems to be working now! :)  :)  i have rebooted a couple of times and all the permisions i changed are intact. 

thanks all very much for your help, i really appreciate it.

cheers
john

---

### Post by johnkabuto on 2005-08-28
h

---

