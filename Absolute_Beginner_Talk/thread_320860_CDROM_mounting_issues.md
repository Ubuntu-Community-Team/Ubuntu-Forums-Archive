---
title: "CDROM mounting issues"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by vierdreieins on 2006-12-18
I've gone through the tags, and it seems like a lot of people are having similar problems in Edgy, but I can't seem to find a solution. 

Basically, music CDs run fine (I haven't tried DVDs yet) so I know it's not the CD-ROM itself,  but when I put a data CD in, no icon appears on the desktop and it won't mount when I try to browse to it through Computer. Then it won't let me eject the CD and I have to reboot just to open it. I was able to browse it once about a week ago, but it locked up mid-transfer and I had to restart. Since then I haven't tried until today.

Any ideas?

---

### Post by pay on 2006-12-18
To mount ```
sudo mount /dev/hdx /media/cdrom0
```to unmount```
sudo umount /dev/hdx /media/cdrom0
```Change hdx to your cdrom (ie hda)

---

### Post by vierdreieins on 2006-12-18
> **pay said:**
> Change hdx to your cdrom (ie hda)

How do I find out which it is?

---

### Post by pay on 2006-12-18
```
sudo fdisk -l | grep iso9660
```or if that doesn't work, look in your fstab```
nano /etc/fstab
```

---

### Post by hal10000 on 2006-12-18
Post the content of your /etc/fstab file. In a terminal window do:[COLOR="Red"]cat /etc/fstab[/COLOR]

---

### Post by vierdreieins on 2006-12-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=713e1ce4-519a-44e0-a000-cf81e6e75cfd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5db4c34c-36da-422d-abbb-4a453c97aa84 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by tommcd on 2006-12-18
So for you it is /dev/hdc /media/cdrom0. To mount:
sudo mount  /dev/hdc /media/cdrom0 
to unmount:
sudo umount /dev/hdc /media/cdrom0

---

### Post by hal10000 on 2006-12-18
But it' strange that a data-CD doesn't get an icon on the desktop. Have you installed the pmount and hal packages?

---

### Post by tommcd on 2006-12-18
Hal,
what are pmount and hal packages, and what are they used for? For what it's worth, I had the same problem mounting data DVD+Rs in zenwalk 4. The data DVDs were all burned in ubuntu. Music CDs and DVD movies played fine. Never figured it out.

---

### Post by pay on 2006-12-18
I've never used pmount, but I use ivman and hal together for automounting.

---

### Post by vierdreieins on 2006-12-18
> **hal10000 said:**
> But it' strange that a data-CD doesn't get an icon on the desktop. Have you installed the pmount and hal packages?

I haven't; didn't know of their existence! Perhaps that will solve my problem. I'll give it a shot sometime soon and see what happens (as well as the terminal mounting trick).

Thanks guys. :D

---

### Post by hal10000 on 2006-12-18
@tommcd:
pmount is a program which permits normal users to mount removable devices.
I have never heard of lvmount, maybe this works,too; but I guess it is not in the ubuntu package tree.

hal stands for "Hardware Abstraction Layer", it makes sure to recognize your hardware at boot-time.

---

