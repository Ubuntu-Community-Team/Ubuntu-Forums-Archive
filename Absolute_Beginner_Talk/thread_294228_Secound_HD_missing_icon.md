---
title: "Secound HD missing /icon"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by deadgobby on 2006-11-06
I mounted my 2cd HD with ease. In the home folder use to be a icon and now it is gone. I used the howto at [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux) and got it to work just fine. After i shut down and got back from work. The HD icon was gone. fdisk get this

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19328   155252128+  83  Linux
/dev/hda2           19329       19457     1036192+   5  Extended
/dev/hda5           19329       19457     1036161   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4831    38804976   83  Linux
/dev/hdb2            4832        4865      273105    5  Extended
/dev/hdb5            4832        4865      273073+  82  Linux swap / Solaris





Just scratching my head how to get into the hd again and transfer data.

THanks

Gobby

---

### Post by taurus on 2006-11-06
Did you mount it to /media?  What does your /etc/fstab look like anyway?

```
more /etc/fstab
```

---

### Post by deadgobby on 2006-11-06
Yea I guess,
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=908e0cb9-b793-4cf6-96a9-f3a5cdcb0f4f /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=5d17a09c-97b5-4d60-bf02-5b4948f8dd21 none            swap    sw            
  0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

THank you for your help :D

---

### Post by taurus on 2006-11-06
> **deadgobby said:**
> Yea I guess,
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=908e0cb9-b793-4cf6-96a9-f3a5cdcb0f4f /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=5d17a09c-97b5-4d60-bf02-5b4948f8dd21 none            swap    sw            
  0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

THank you for your help :D
So, looks like you mount /dev/hdb1 by hand then!!!  Does /dev/hdb1 contain another Linux distro?  Where do you want to mount it because you can add an entry in /etc/fstab and have it mount automatically upon boot.

What's the output of this command then?

```
df -h
```

---

### Post by deadgobby on 2006-11-06
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             146G  3.7G  135G   3% /
varrun                173M   84K  173M   1% /var/run
varlock               173M     0  173M   0% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm                173M     0  173M   0% /dev/shm
lrm                   173M   18M  156M  10% /lib/modules/2.6.17-10-generic/volatile

---

### Post by taurus on 2006-11-06
Okay, I will assume you want to mount /dev/hdb1 to /media/other_distro with ext3 filesystem.  Open a terminal and bring up an editor to edit your /etc/fstab.  Of course, make a back up copy first just in case...

```

sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```
Now, add the following line to the end of it.

```

/dev/hdb1   /media/other_distro   ext3   defaults   0   1

```
Save it and then create a mount point for it and mount it.

```

sudo mkdir /media/other_distro
sudo mount -a
df -h  <-- you will now see /dev/hdb1 on /media/other_distro...

```

---

### Post by deadgobby on 2006-11-06
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             146G  3.7G  135G   3% /
varrun                173M   84K  173M   1% /var/run
varlock               173M     0  173M   0% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm                173M     0  173M   0% /dev/shm
lrm                   173M   18M  156M  10% /lib/modules/2.6.17-10-generic/volatile
/dev/hdb1              37G   15G   20G  43% /media/other_distro

  Cool. Now I how can I get to list files and/or an icon for the drive. It is a drive with ubie on it. Just like to transfer file. thank you for you help. 
BIG THANKS :p

---

### Post by taurus on 2006-11-06
I guess everything is working fine now for you now!

---

### Post by deadgobby on 2006-11-06
when I go to home folder and computer
. The secound drive is not listed. Only the file system of the 1st drive.
Gobby

---

### Post by taurus on 2006-11-06
> **deadgobby said:**
> when I go to home folder and home. The secound drive is not listed. Only the file system of the 1st drive.
Gobby
:confused: 

Not sure exactly what you mean here!  The second drive is currently mounted on /media/other_distro, not in your $HOME.

---

### Post by deadgobby on 2006-11-06
OK Found it!! Thank you very much and I summons the good day fairies to bring  a good day to you.
Gobby:mrgreen:

---

