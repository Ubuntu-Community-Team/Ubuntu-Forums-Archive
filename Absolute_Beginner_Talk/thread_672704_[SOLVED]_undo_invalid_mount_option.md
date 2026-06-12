---
title: "[SOLVED] undo invalid mount option"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by worksofcraft on 2008-01-19
I added a previously used ubuntu disk to my PC as hdb and it's volumes (hdb1, hdb2 and hdb3) showed up in the disk mounter on the panel. There was no problem reading the files there... until I decided to change the mount options so that I might also have write access to them. Evidently I messed up because now it won't mount, saying "invalid mount option".

I can't work out how to undo my mistake as it doesn't appear to be in /etc/fstab. Where should I be looking?

---

### Post by pollywog on 2008-01-20
How did you change the permissions? Are these all Ext3 partitions? It might be helpful to post the contents of /etc/fstab as well as the result of typing the following in the terminal
```
sudo fdisk -l
```

---

### Post by UltraMathMan on 2008-01-20
I did the same thing to an ipod once - you right clicked the drive and changed the options under properties, right? Do ```
sudo fdisk -l
``` and find the device, then mount it ```
sudo mount /dev/device /media/mountfolder
``` From there it should pop up on the desktop again so you can right click on it again and remove the mount options you added.

-Hope this helps :)

---

### Post by pollywog on 2008-01-20
The following link should take you to an excellent tutorial that explains the best procedure for permanently mounting Linux partitions. It seems that most of the advice you'll find floating around out there is pertaining to mounting windows partitions, not Linux ones.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by worksofcraft on 2008-01-20
fdisk -l didn't show anything unexpected... Incidentally in case anyone else reading this U need to put sudo in front of commands to run them as root and the partitions (like/dev/hdb1) on a disk don't contain a valid partition table as that is on the whole disk only (/dev/hdb) 

Anyway, so I manually mounted the disk with mount command as suggested. Sure enough it appeared on the desk top and I could right click it then, select "properties" then "drive" and delete the faulty mount options I had added. Now I can mount it from the panel as before.
:guitar: That rocks thanks :-)

... and I'll study that tutorial in detail before messing it up again :popcorn:

---

