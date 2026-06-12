---
title: "Mount NTFS over network with write permission"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by routerstu on 2007-04-10
hi all, i have a dlink dns323 and was using

sudo mount -t smbfs //192.168.1.50/Volume_1 /media/Music -o username=music,password=passwd

to mount the volume, but i dont seemt o have write permissions.  does anyone know how i can do this with ntfs-3g or how i can add something like this to fstab?  i see many exmaples of usb/attached drives but not network, especially with alternative credentials.

thank you

---

### Post by BillinDetroit on 2007-04-11
I am not certain that it is possible to write to a NTFS partition. Read - yes. Write - no. Something about copyrights or patents or black helicopters ... I forget just which.

---

### Post by devnulljp on 2007-04-11
You need to specify the share as writable -- it doens't matter what the filesystem is when mounting across the network; there are probs with writingto ntfs but only if mounting locally.
Have a look here: [http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)
and here: [http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

---

### Post by routerstu on 2007-04-11
i could have sworn this worked with my normal command.  has no one else mounted a share over a network with write access?

---

### Post by devnulljp on 2007-04-14
> **routerstu said:**
> i could have sworn this worked with my normal command.  has no one else mounted a share over a network with write access?
Yes, see my post above. The filesystem is irrelevant when mounting over the network  though -- it doesn't matter if it's ntfs, vfat, ext2/3, whatever, but it has to be shared and mounted as writable.

---

### Post by routerstu on 2007-04-14
Thank for your help!!!

i also used this

[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently#Mounting_smbfs_Shares](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently#Mounting_smbfs_Shares)


the command i used exactly was:

mount -t smbfs //192.168.1.50/Volume_1 /media/Music -o username=music,password=music,gid=jason,fmask=775

---

