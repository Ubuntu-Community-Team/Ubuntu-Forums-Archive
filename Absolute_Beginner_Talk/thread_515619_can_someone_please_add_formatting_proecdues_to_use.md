---
title: "can someone please add formatting proecdues to user guide"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-08-02
The user guide im referring to is here
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

i had added a 80 gig sata drive. i can not for the life of me figure out how to format/partition the thing, but i did d/l the[ gparted live cd.]("http://gparted.sourceforge.net/livecd.php")

this did allow me to see the sata hdd and partition it as well.

in case there are newbies like myself this info will come in handy
primary master hard drive is /dev/hda
primary slave is /dev/hdb
secondary master is /dev/hdc
secondary slave is /dev/hdd

and if you have a sata drive the first one is /dev/sda
i only have one but i would assume the second sata drive would be /dev/sdb

can someone please add how to partition and format new drives in linux format easily enough for newbies like me to understand.

At this point in time i have the 80 gig hdd readable, but it had a padlock on it and it says i can not do anything to it as im not "root"

*sigh* 

KISS

Keep it simple stupid my dad always used to say

---

### Post by Seisen on 2007-08-02
Ask a mod to move your post to here.

[http://ubuntuforums.org/forumdisplay.php?f=78]("http://ubuntuforums.org/forumdisplay.php?f=78")

This way at least your request will be heard.

---

### Post by ramjet_1953 on 2007-08-02
Don't forget, you cannot make any changes to a disk that is mounted.

Your best bet is to download the [COLOR="Blue"]GPartEd LiveCD iso[/COLOR] and burn that image to a CD.

You then boot from the CD and you can partition to your heart's content.

You can get the iso from here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Regards,
Roger :cool:

ps Don't forget, when burning the iso do it SLOWLY, no faster than 4 X.

---

### Post by stinger30au on 2007-08-02
I did d/l the gparted disc and it ran nicely.i setup the new sata80gig drive no worries and set it up as ext3.
but when i get back in to ubuntu the disc has a gold/yellow padlock on it and wont allow me to do anything with the drive as it says im not root.

is there something i missed doing in gparted???

---

### Post by bodhi.zazen on 2007-08-02
> **stinger30au said:**
> The user guide im referring to is here
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

As far at I know, that site is not maintained by Ubuntu.

> i had added a 80 gig sata drive. i can not for the life of me figure out how to format/partition the thing, but i did d/l the[ gparted live cd.]("http://gparted.sourceforge.net/livecd.php")

this did allow me to see the sata hdd and partition it as well.

in case there are newbies like myself this info will come in handy
primary master hard drive is /dev/hda
primary slave is /dev/hdb
secondary master is /dev/hdc
secondary slave is /dev/hdd

and if you have a sata drive the first one is /dev/sda
i only have one but i would assume the second sata drive would be /dev/sdb

can someone please add how to partition and format new drives in linux format easily enough for newbies like me to understand.

At this point in time i have the 80 gig hdd readable, but it had a padlock on it and it says i can not do anything to it as im not "root"

*sigh* 

KISS

Keep it simple stupid my dad always used to say

LOL

Partitioning : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

Permissions : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Follow the links in my sig for additional information.

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by stinger30au on 2007-08-03
thanks for the info.i wont have time to look at the hdd tonight, but will do it in morning

---

