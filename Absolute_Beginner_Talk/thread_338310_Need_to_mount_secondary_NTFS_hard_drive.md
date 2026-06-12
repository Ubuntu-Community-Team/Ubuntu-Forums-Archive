---
title: "Need to mount secondary NTFS hard drive"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by atarileaf on 2007-01-14
Hello. I've got an 80 gig drive that currently has some data that I wish to retrieve to back it up. It is set up as secondary master and still has XP on it but I can't access the files because Ubuntu tells me its unable to mount the drive with these errors:

error: device /dev/hdc1 is not removable

error: could not execute pmount

I simply want to access the data and upload it to an online backup service but need to know how to "mount" the drive properly so Ubuntu can access the files.

Thanks

---

### Post by taurus on 2007-01-14
Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hdc1 /media/windows -o nls=utf8,umask=0222
df -h
```

---

### Post by atarileaf on 2007-01-14
That worked. Thanks very much.

Can I ask a question? How did you learn for yourself that command? It seems so obscure. I certainly wouldn't be able to remember that string.

---

### Post by taurus on 2007-01-14
From reading and playing around.

---

### Post by cliveo on 2007-01-14
You can also mount the ntfs drive on startup (read only by editing the /etc/fstab file- use terminal and write sudo gedit /etc/fstab
Now fstab opens in gedit add the line 
/dev/Hdb1(or whatever)       /media/windows    ntfs    defaults,utf8,umask=0022,gid=0 0       1

You might want to type first in terminal as an insurance   
cp /etc/fstab /etc/fstab.copy

---

### Post by taurus on 2007-01-14
> **cliveo said:**
> You can also mount the ntfs drive on startup (read only by editing the /etc/fstab file- use terminal and write sudo gedit /etc/fstab
Now fstab opens in gedit add the line 
/dev/Hdb1(or whatever)       /media/windows    ntfs    defaults,utf8,umask=0022,gid=0 0       1

You might want to type first in terminal as an insurance   
cp /etc/fstab /etc/fstab.copy

```
sudo cp /etc/fstab /etc/fstab.copy
gksudo gedit /etc/fstab
```
```
/dev/hdc1   /media/hdc1   ntfs   nls=utf8,umask=0222   0   0
```

---

### Post by Monker on 2007-01-14
Hi there,

I am completely new to linux and have gone through a few other distro trying to find one taht was gentle on me. Ubuntu seems to fit the bill :)

Just a quick question on you clever plps responses ;) Am I correct in assuming that in order to mount a physical device you have to create a directory to mount it into? If this is the case then I am interested to know how my USB memory stick actually manages to just work when I plug it in as Ubuntu can't have known anything about it before I plugged it in. I ask this possibly silly question because on previous unfriendly linux distro's (Unfriendly to newbies I mean, I am sure they are great for those who know what they are doing) It took me ages to get my memory stick working, only for it to forget on a reboot.

Thanks for you time :)

Monker

---

### Post by taurus on 2007-01-14
Because there is (or it will be created on the fly by the system) already a mount point called /media/usbdrive.  That's where your USB stick probably gets mounted to.

---

### Post by luishrd on 2007-01-14
Hello there, another green one here...

so there is no user friendly way to have Ubuntu just "see" the ntfs drives on my system on start up? ( I have 3 hdd, 1 SATA formatted as NTFS for WinXP, 1 master IDE used for Ubuntu 6.1 and 1 slave IDE formatted as NTFS as well for Docs).

I ask this because on my reading around the net looking for a Linux distro to try, I read about some  of them booting up and seeing the windows partitions out of the box, cant remember which was it, maybe mandriva and freespire, not sure.

Anyway, all those commands and terminal look scary for the complete noob, maybe a complete noob shouldnt be installing Linux in the first place :( 

thanks

---

### Post by taurus on 2007-01-14
If you want to mount those drives, I will walk you through it.  It's up to you.  Terminal is not that scary at all if you know what command to type.

---

### Post by luishrd on 2007-01-14
> **taurus said:**
> If you want to mount those drives, I will walk you through it.  It's up to you.  Terminal is not that scary at all if you know what command to type.

Sure mate!

If you have the time, I would greatly appreciate it.

Thanks

---

### Post by taurus on 2007-01-14
Okay, will see what we can do here.

Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
sudo fdisk -l
```
(That would be letter l as in larry at the end of that command.)

---

### Post by luishrd on 2007-01-14
Since someone said that in order to mount volumes you need to create folders and mount the drives to those folders, I created two folders using the 'Places' > 'Home Folder' Graphical Tool, named them SATA and Docs...

Is that necessary?

Thanks

---

### Post by luishrd on 2007-01-14
here we go...

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4661    37439451   83  Linux
/dev/hda2            4662        4863     1622565    5  Extended
/dev/hda5            4662        4863     1622533+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+   7  HPFS/NTFS



thats it.

over...

---

### Post by taurus on 2007-01-14
So you want to mount both /dev/hdb1 & /dev/sda1.  From a terminal, type

```
gksudo gedit /etc/fstab
```
Scroll to the end and add the following two lines.

```

/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda1   /media/sda1   ntfs    nls=utf8,umask=0222   0   0

```
Save it.  Now, create two new mount points and mount them.

```
sudo mkdir /media/hdb1 /media/sda1
sudo mount -a
df -h
```

---

### Post by luishrd on 2007-01-14
cool, the IDE drive is mounted but the SATA drive returns this error:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


thanks

---

### Post by luishrd on 2007-01-14
the df -h command returns:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.1G   32G   6% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/hdb1              75G   49G   26G  66% /media/Docs

---

### Post by taurus on 2007-01-14
Can I have a look at your /etc/fstab again?

```
cat /etc/fstab
```

---

### Post by luishrd on 2007-01-14
there:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=88299ffd-22e1-4162-850a-b411d357a94a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c73d3f44-76a3-4a7e-ae28-3564129b11cf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /media/Docs ntfs nls=utf8,umask=0222 0 0
/dev/sda1 /media/SATA ntfs nls=utf8,umask= 0222 0 0

---

### Post by taurus on 2007-01-14
You have an extra space between **umask=** and **0222** for /dev/sda1!

```
/dev/sda1  /media/SATA  ntfs  nls=utf8,umask= 0222  0  0
```

---

### Post by luishrd on 2007-01-14
That did it, sorry about that... LOL](*,) 

Thanks!!!

It works, now on to reboot and check its still there....


Thanks again.

---

### Post by taurus on 2007-01-14
They both will always be where they should be each time you boot.  And you still think a terminal is a scary thing!  ;)

---

### Post by luishrd on 2007-01-14
Beautiful, 2 down, plenty to go... next step Media players for my MP3s... hope no more Terminal lol

Thanks again.

---

### Post by taurus on 2007-01-14
Better hold that thought for a while!!!  What media players are you talking here?  You can probably search for them in synaptic:  System -> Administration -> Synaptic Package Manager.

---

### Post by luishrd on 2007-01-14
I PMed you instead if thats ok with you, I think is better that way so we keep this thread on subject.

---

### Post by Buck2348 on 2007-01-14
> so there is no user friendly way to have Ubuntu just "see" the ntfs drives on my system on start up?I've done about four installs of Ubuntu, all on the same machine, and always both of my hard disks and all seven partitions are seen and mounted automatically.  I was using the desktop install with an .iso image, and of course alll the partitions were set up in the preliminary part of that by Gparted.  Taurus, is there a cli command that shows information about all disks, or all connected devices, whether they are mounted or not?

Thanks,
Buck

Edit--  Sorry, didn't mean to butt in.  I was on page one and didn't notice there were two more.

---

### Post by taurus on 2007-01-14
> **Buck2348 said:**
> I've done about four installs of Ubuntu, all on the same machine, and always both of my hard disks and all seven partitions are seen and mounted automatically.  I was using the desktop install with an .iso image, and of course alll the partitions were set up in the preliminary part of that by Gparted.  Taurus, is there a cli command that shows information about all disks, or all connected devices, whether they are mounted or not?

Thanks,
Buck

Edit--  Sorry, didn't mean to butt in.  I was on page one and didn't notice there were two more.

Here you go.

```
sudo fdisk -l
```

---

### Post by Buck2348 on 2007-01-14
Thanks--don't know why I didn't see that before.

---

### Post by Buck2348 on 2007-01-14
Taurus, if you're still here-- why were luishrd's disks not mounted automatically, do you know?  He didn't connect them after installing Ubuntu did he?

Thanks,
Buck

---

### Post by taurus on 2007-01-14
> **Buck2348 said:**
> Taurus, if you're still here-- why were luishrd's disks not mounted automatically, do you know?  He didn't connect them after installing Ubuntu did he?

Thanks,
Buck

They usually don't mount automatically unless you tell the installer to mount them when you get to the partition step.

---

### Post by Buck2348 on 2007-01-14
> **taurus said:**
> They usually don't mount automatically unless you tell the installer to mount them when you get to the partition step.
OK, thanks.  I must have told it to do that.

Buck

---

