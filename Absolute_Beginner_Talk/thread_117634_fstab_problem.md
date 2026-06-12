---
title: "fstab problem"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by lemmy999 on 2006-01-15
On shutdown I have noticed that the comment "Line 2 of /etc/fstab is bad". The machine seems to run Ok but I'm concerned that it may affect something in the future. I think the problem arose when I tried to mount a Windows partition and had to edit /etc/fstab. I did backup the original fstab. Can i use that to restore? Will using it mean that i wont be able to see my windows partition?

Output for current fstab is


 /etc/fstab: static file system information.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1


/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda6 /media/hda6 vfat rw,user,fmask=0111,dmask=0000 0 0

---

### Post by AlanQ on 2006-01-15
Hi Lemmy

Try putting a hash (#) in front of the line that reads:
 /etc/fstab: static file system information.

ie
```
# /etc/fstab: static file system information.
```

Alan

---

### Post by lemmy999 on 2006-01-15
Alan

Worked a treat! 

thanks
Lemmy

---

