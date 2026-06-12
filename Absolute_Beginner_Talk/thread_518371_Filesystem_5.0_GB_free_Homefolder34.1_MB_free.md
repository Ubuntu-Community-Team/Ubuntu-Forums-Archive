---
title: "Filesystem: 5.0 GB free Homefolder:34.1 MB free???"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by jojohippo on 2007-08-05
Hi, I'm running ubuntu using [Wubi]("http://wubi-installer.org/") but I think this is a ubuntu problem not a wubi one...

When I navigate to the top of my folder tree it says I have 5.0 GB of free space on my harddrive. However when I go to my Home folder (\home\joe\) it says only 34.1 MB. And whenever I try to save stuff in my home folder or any of its directories (like the desktop), theres no free room.

I only have one user account (is that what its called in ubuntu?). I would like to make the amount of space in my home folder the same as the space in my root folder. Thanks in advance.

---

### Post by skymera on 2007-08-05
i dont understand wubi.

it installs on a windows partition which is sily.

have you tried clearing out your 'Home'?

---

### Post by jojohippo on 2007-08-05
Well I've tried clearing out a few larger files to create some room.. but the problem is there is 5 gigs of unused space on the partition but for some reason my home folder can't access it.
WUBI's nice for the noobs like me who just want an introduction to ubuntu =)

---

### Post by dougfractal on 2007-08-05
more info please

df -h
du -sh ~/

---

### Post by hardyn on 2007-08-05
why are you able to elminate wubi as a cause of the problems?

---

### Post by alienexplorers on 2007-08-05
Enter in terminal > sudo fdisk -l and post the output here.

---

### Post by jojohippo on 2007-08-06
Here you go... and no I wasn't able to eliminate wubi as the source of the problems, but i've run ubuntu virtually before and never encoutered this problem... i guess i could be wubi though.


~$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/media/host/wubi/disks/system.virtual.disk
                      7.8G  2.5G  5.0G  33% /
varrun                248M  100K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb            248M  104K  248M   1% /proc/bus/usb
udev                  248M  104K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   33M  215M  14% /lib/modules/2.6.20-16-generic/volatile
/media/host/wubi/disks/home.virtual.disk
                      939M  567M  325M  64% /home



 du -sh ~/

550M    /home/joe/



sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3854    30957223+   7  HPFS/NTFS
/dev/sda2   *        3855        9729    47190937+   7  HPFS/NTFS

---

### Post by alienexplorers on 2007-08-06
Under what drive is ubuntu under?

---

### Post by dougfractal on 2007-08-06
> /media/host/wubi/disks/system.virtual.disk
7.8G 2.5G 5.0G 33% /

/media/host/wubi/disks/home.virtual.disk
939M 567M 325M 64% /home

It says you've got 325MB free in your /home
and 5GB free in your /

```
sudo mkdir /mnt/homeextra/
sudo chown 1000:1000 /mnt/homeextra   # username:username
ln -s /mnt/homeextra ~/homeextra
```

you now have 5GB space in your homeextra folder

---

### Post by jojohippo on 2007-08-09
Thanks dougfracta :KSl... now I have a shortcut to the homeextra folder within my home folder and it has 5 gb free. It's not perfect but it does the job.
This is way better than toshiba support for windows (they told me to reinstall windows when all that was necessary was reinstalling a driver)

---

