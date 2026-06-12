---
title: "fstab text question"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by basho007 on 2007-03-04
I've just installed Edgy on a dual Windows XP boot.  At installation the fstab that was created did not pick up  the two windows partitions.    I've been rooting about and arrived at the point where I think I'm about to actually commit to changing the fstab so each partition mounts on boot. have made a back-up of fstab,  have created the mount folders

 before I actually take the plunge, I wonder if anyone could spot any errors in the two lines I propose to put into fstab?

ADDING TO FSTAB: 


/dev/hda1	/media/WinOper	ntfs iocharset=utf8,rw,users,gid=users,umask=000, 0 0

/dev/hda2	/media/WinLin	vfat iocharset=utf8,rw,users,gid=users,umask=000, 0 0

Should umask be 000 or 0000?  
Should there be commas before the second last "0"s or spaces?    
is it better to use the UUID= method?

thanks 

basho007

---

### Post by klein de usa on 2007-03-04
hi
when i installed edgy, with xp .mine were auto mounted, my drives are sata and the two xp partions were hdo,1 and hdo,2 acording to grub but in edgy they show up as :

/dev/sda1
/dev/sda2

that is all that was in my fstab and at boot time they mounted and put icons on my desk top in edgy.
hope this helps

---

