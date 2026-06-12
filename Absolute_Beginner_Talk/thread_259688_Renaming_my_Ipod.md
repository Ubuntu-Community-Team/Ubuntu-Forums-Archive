---
title: "Renaming my Ipod"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-17
When I connect my ipod, it is listed with the name that my sister named the ipod.  Is there any way I can change it?  Thanks.

---

### Post by 3rr0r on 2006-09-17
shameless bump

---

### Post by 3rr0r on 2006-09-18
to the top !

---

### Post by 3rr0r on 2006-09-19
bump

---

### Post by 3rr0r on 2006-09-20
?

---

### Post by crokett on 2006-09-20
> **3rr0r said:**
> When I connect my ipod, it is listed with the name that my sister named the ipod.  Is there any way I can change it?  Thanks.

assuming ubuntu sees it as a new filesystem, you can unmount it and mount it under a different name. 

```

sudo umount 

sudo mount 


```

check /etc/fstab to see if it is automounted.  if so, you need to edit that entry as well

---

### Post by 3rr0r on 2006-09-21
This is what my fstab looks like, I don't see the ipod listed

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ext3    defaults        0       2
/dev/sda4       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

sda 3 - root
sda 4 - swap
sda 2 - my other linux os
sda 1 - win xp

How do I umount/mount my ipod so I can rename it, if I don't see it?

---

### Post by aysiu on 2006-09-21
Maybe I'm being a bit naive, but can't you just F2 and then rename the icon...?

---

### Post by 3rr0r on 2006-09-21
> **aysiu said:**
> Maybe I'm being a bit naive, but can't you just F2 and then rename the icon...?

I had my ipod on the desktop highlighted and hit f2 and nothing happened.

[IMG]http://i53.photobucket.com/albums/g56/learntobndg/ipod.png[/IMG]

---

### Post by dextur on 2007-09-23
Did anyone succeed? I have not found any information on the net on how to do this.

---

### Post by Brindley on 2007-10-05
I used the tool mlabel from the package mtools.

Install mtools
```
 sudo apt-get install mtools
```

Plug in your ipod and find out the device location
```
 cat /etc/mtab 
```  

Look for the entry that says something like 
```
/dev/sdc2 /media/IPOD vfat rw,nosuid,nodev,shortname=mixed,uid=1001,utf8,umask=077 0 0 
```
In my case the relevant bit was /dev/sdc2

Add an entry in the mtools config file for the device
```
sudo gedit /etc/mtools.conf
```
Add a line at the bottom, in my case it was 
```
drive f: file="/dev/sdc2"
```
and save the file.

Finally, run mlabel.
```
sudo mlabel f:
```
If all goes well, it should tell you the current name of the device and ask for a new one.

Hope that makes sense, if you need any more help feel free to ask. And if anyone knows a better way, please do share! :)

---

### Post by zach12 on 2007-10-05
Hi can i put mp3's on my ipod and when i put mp3s on using  illtunes:confused::confused:
will it get rid of them

thanks

---

### Post by Niklas Schröder on 2007-12-04
i get...

```

niklas@nik:~$ sudo mlabel i:
Total number of sectors not a multiple of sectors per track!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test

```

why?

---

### Post by nikoPSK on 2007-12-04
Yay! so I can rename my second gen ipod I got second hand?:confused:

---

### Post by cypresstwist on 2008-02-09
Great tip. Helped me alot with my 1GB white Nano

---

