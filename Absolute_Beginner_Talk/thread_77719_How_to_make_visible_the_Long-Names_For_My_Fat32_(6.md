---
title: "How to make visible the Long-Names For My Fat32? (6-8chars maxi only :-(  )"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-17
I wish to have longer name for my fat32 than 8chars ...

is it possible to do sthg ??

thank a lot !!

pat'

---

### Post by Pablo_Escobar on 2005-10-17
Do You mean the file names at Your FAT32 partitions ?
If so, then it's easily available.
Post Your fstab file here to troubleshoot.

---

### Post by daoc on 2005-10-17
no i dont think so buddy, fat32 doesnt support long file names. im a bit gutted about it too.

---

### Post by Pablo_Escobar on 2005-10-17
[QUOTE=daoc]no i dont think so buddy, fat32 doesnt support long file names. im a bit gutted about it too.[/QUOTE]

Heck, how FAT32 does not support long filenames :confused: 
I have 3 mounted FAT32 partitions, lots of files on them have > 8 chars at filenames. I can create those files on these partitions, edit them, execute them. 
If they are available in Window$ then they're in Linux :D

---

### Post by patrick295767 on 2005-10-17
[QUOTE=Pablo_Escobar]Do You mean the file names at Your FAT32 partitions ?
If so, then it's easily available.
Post Your fstab file here to troubleshoot.[/QUOTE]

This evening, I'll post you my /etc/fstab

Na razie (see ya') !!

Thank you very much 

Pat'

---

### Post by patrick295767 on 2005-10-17
[QUOTE=patrick295767]This evening, I'll post you my /etc/fstab

Na razie (see ya') !!

Thank you very much 


Pat'[/QUOTE]
  
   

   

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hda3	/mnt/hda3	ntfs	defaults,rw,user,umask=000	0	2
/dev/hda1	/mnt/hda1	msdos	defaults,rw,user,umask=000	0	0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5	/mnt/hda5	ntfs	defaults,rw,user,umask=000	0	2
/dev/hdc	/mnt/hdc	auto	user,noauto,ro,unhide	0	1
/dev/sda1	/mnt/sda1	auto	defaults,rw,user	0	1
//10.x.x.x/user /mnt/smb_user smbfs credentials=/root/samba/.smbpwd 0 0

---

### Post by Pablo_Escobar on 2005-10-18
Pat, 

1. Why msdos and not vfat on Your hda1 ? What type of partition is it ?
2. What are hdc and sda1 - I presume that they're burners, but I want to make sure.

---

### Post by patrick295767 on 2005-10-18
[QUOTE=Pablo_Escobar]Pat, 

1. Why msdos and not vfat on Your hda1 ? What type of partition is it ?
2. What are hdc and sda1 - I presume that they're burners, but I want to make sure.[/QUOTE]


1/
sda1 is a fat16 

(sometimes, i am using FAT32 with usb key and I also mount -t msdos I guess)

I 'll try mount -t vfat ... & let you know about my progress !!
  
  
2/ hdc is my DVD/CD burner 
        
and sda1 is an external Qtec rack [http://www.qtec.info/products/product.htm?artnr=13278](http://www.qtec.info/products/product.htm?artnr=13278)
with inside a CD Burner
 
 Thank you very much !!!

Papa (see ya')

Patrick

---

### Post by patrick295767 on 2005-10-18
the reply : vfat is the key !!



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hda3	/mnt/hda3	ntfs	defaults,rw,user,umask=000	0	2
/dev/hda1	/mnt/hda1	vfat	defaults,rw,user,umask=000	0	0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5	/mnt/hda5	ntfs	defaults,rw,user,umask=000	0	2
/dev/hdc	/mnt/hdc	auto	user,noauto,ro,unhide	0	1
/dev/sda1	/mnt/sda1	vfat	defaults,rw,user	0	1



So, now, I can read loong names !!

Thank you linux community !!

---

