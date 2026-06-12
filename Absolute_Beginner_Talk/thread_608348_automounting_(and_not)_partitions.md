---
title: "automounting (and not) partitions"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Cpt Black on 2007-11-09
Hi,

I have 4 data partitions on my system, 2 booting windows and ubuntu, one my home partition and one a shared data partition (plus swap).

Currently, when I boot into ubuntu, I am able to access my ubuntu partition and home dir (which is fine) but not the the shared data partition without manually mounting it first. Also, I have access to the windows partition and would like to stop that in case some else uses my computer and messes it up accidentally.

Below is my fstab and the partition list from gparted

sda1 - windows
sda2 - ubuntu "/""
sda3 - extended??
 >sda5 - "home"
 >sda6 - swap
sda4 - shard "Data"

sda5 and sda6 appear to be nested within sda3 when seen in gparted though this doesn't appear to affect anything at the moment

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=633757c3-a6e9-4fb4-a3c8-ef391595a581 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7a051556-96ad-4125-b8e4-2f3f37e9b443 /home           ext3    defaults        0       2
# /dev/sda1
UUID=3ACC8F1BCC8ED095 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=8595-F206  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=f5fec2c1-3100-482e-ad99-ed8fd1e318d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Cheers,
CB

edit: P.S. the shared data partition is formatted in ntfs - which I can access when its mounted, along with other ntfs partitions and external hdds

---

### Post by positroniks on 2007-11-09
I just went through this today myself. The answer, for me at least, was this:

Go to System>Administration>Synaptic Package Manager
Search for pysdm and install it
Go to System>Administration>Storage Device Manager
Click on each partition in the left panel and set it up however you want

The next time you reboot all the partitions you setup to mount should be automounted and showing on your desktop. Hope this helps :)

---

### Post by girard on 2007-11-27
so did pysdm work? i need to control the automounting of partitions based on user account also. i have an admin account which i use, and a guest account. problem is, i don't want my partition to mount when guest account logs in, but i want it to automount with admin. 

any ideas?

---

### Post by Cpt Black on 2007-11-27
I managed to get my extra partition to automount, but haven't stopped the windows partition from mounting yet.

---

### Post by fineas on 2007-11-27
Right click on a panel> add to panel. The last object about mounting or unmounting disks might help.

---

### Post by The other One on 2007-11-30
> **positroniks said:**
> I just went through this today myself. The answer, for me at least, was this:

Go to System>Administration>Synaptic Package Manager
Search for pysdm and install it
Go to System>Administration>Storage Device Manager
Click on each partition in the left panel and set it up however you want

The next time you reboot all the partitions you setup to mount should be automounted and showing on your desktop. Hope this helps :)

Thanks, Positronics, this solved my mounting problem too.:guitar:

---

### Post by A$h X on 2007-12-19
> **positroniks said:**
> I just went through this today myself. The answer, for me at least, was this:

Go to System>Administration>Synaptic Package Manager
Search for pysdm and install it
Go to System>Administration>Storage Device Manager
Click on each partition in the left panel and set it up however you want

The next time you reboot all the partitions you setup to mount should be automounted and showing on your desktop. Hope this helps :)

Thank you so much, I was having MAJOR problems with getting a partition to mount at boot. This just solved all my problems!

---

### Post by Inxsible on 2007-12-19
> **girard said:**
> so did pysdm work? i need to control the automounting of partitions based on user account also. i have an admin account which i use, and a guest account. problem is, i don't want my partition to mount when guest account logs in, but i want it to automount with admin. 

any ideas?you can simply change the ownership of the mount point to yourself. That way, even if it mounts under another username, they will not be able to access it.

---

### Post by Inxsible on 2007-12-19
/windows not mounting may be due to the fact that it has ntfs file system and you are trying to mount it as vfat. I am not sure if that would work. It probably doesn't.

But I'm glad you got it working through other means :)

---

### Post by Inxsible on 2007-12-19
> **Cpt Black said:**
> I managed to get my extra partition to automount, but haven't stopped the windows partition from mounting yet.you can stop the windows partition from automounting, by using the 'noauto' option in the fstab

---

### Post by jatatar on 2008-03-31
can't you simply comment out (place a # in front of) the corresponding UUID entry to your windows partition? or use the noauto option so it is available for root?

---

### Post by grozni on 2008-05-08
How can I hide partion from computer:/// I only want to hide them, but still have normal access to them with automount option. Thanks

---

