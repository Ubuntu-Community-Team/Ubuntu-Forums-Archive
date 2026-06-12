---
title: "automount?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Angry penguin on 2007-02-01
I just formatted a disk in fat32 format so i can use it inside windows and ubuntu. It is not automounting at startup so i was wondering what I need to do to get ubuntu to mount this partition on startup?

thanks.

---

### Post by tonyr1988 on 2007-02-01
Open a terminal and type:

> sudo cp /etc/fstab /etc/fstab.backup
sudo cat /etc/fstab

And paste the contents into a reply. That's the file you'll need to edit - we can help you with what you'll exactly need to do if we can see it.

---

### Post by danoyoto on 2007-02-01
> **tonyr1988 said:**
> Open a terminal and type:



And paste the contents into a reply. That's the file you'll need to edit - we can help you with what you'll exactly need to do if we can see it.

Here's mine.  I have the same issue.  I have two drives I'd like to automount.  Both are NTFS right now.  One is a seperate drive and the other is another partition on the same drive ubuntu is on.  Any help is appreciated.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=aeb6675e-abfd-4b23-b980-b7741c3b917e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4f3292a1-4947-4f08-9952-b799539c3b7f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by tonyr1988 on 2007-02-01
Oops - I forgot, could you guys also post the result from:

> sudo fdisk -l

? It'll tell us your partition scheme.

P.S. That's a lowercase L, not a 1.

---

### Post by Angry penguin on 2007-02-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2 -- converted during upgrade to edgy
UUID=af0a308f-ae2b-43b9-a591-657ec13f881d / ext2 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=5A48602E48600B59 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdd1 -- converted during upgrade to edgy
UUID=48281C8C281C7AE0 /media/hdd1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdc5 -- converted during upgrade to edgy
UUID=e068d356-ca33-419b-97f3-cdbdf975167f none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3860    31005418+   7  HPFS/NTFS
/dev/hdc2            3861        7344    27985230   83  Linux
/dev/hdc3            7345        7476     1060290    f  W95 Ext'd (LBA)
/dev/hdc5            7345        7476     1060258+  82  Linux swap / Solaris

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       36483   293049666   8e  Linux LVM

---

### Post by MosesS on 2007-02-02
Having the same issue here:) My other disk that has windows on with another 2 partitions cannot be seen

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2c608a2b-ea3a-4a37-aabb-79802ebd868d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=96735a7f-a215-4c0d-8a25-6909152cf798 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0



and my fdisk

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19929   119121975    f  W95 Ext'd (LBA)
/dev/sda5            5100       15935    87040138+   7  HPFS/NTFS
/dev/sda6           15936       19929    32081773+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30024   241167748+  83  Linux
/dev/sdb2           30025       30401     3028252+   5  Extended
/dev/sdb5           30025       30401     3028221   82  Linux swap / Solaris

---

### Post by Angry penguin on 2007-02-02
i just formatted the drive fat32 and did those commands again. The first time I formatted using the Gparted boot cd and ubuntu didnt recognize the filesystem type. SO I formatted it using gparted inside ubuntu and now it recognizes it as fat32, but i still don't think its mounted. its a 300gb volume.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2 -- converted during upgrade to edgy
UUID=af0a308f-ae2b-43b9-a591-657ec13f881d / ext2 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=5A48602E48600B59 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdd1 -- converted during upgrade to edgy
UUID=48281C8C281C7AE0 /media/hdd1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdc5 -- converted during upgrade to edgy
UUID=e068d356-ca33-419b-97f3-cdbdf975167f none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3860    31005418+   7  HPFS/NTFS
/dev/hdc2            3861        7344    27985230   83  Linux
/dev/hdc3            7345        7476     1060290    f  W95 Ext'd (LBA)
/dev/hdc5            7345        7476     1060258+  82  Linux swap / Solaris

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       36483   293049666    b  W95 FAT32

---

### Post by bodhi.zazen on 2007-02-02
When you re-formatted the drive you changed the uuid.

Either update the uuid or use this:

> /dev/hdd1 /media/hdd1 auto auto,nls=utf8,umask=007,gid=46 0 1

You need to change "ntfs" to either auto or vfat.

See here for reference: [http://www.ubuntuforums.org/showthread.php?&t=283131](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Angry penguin on 2007-02-07
When i entered the command I used sudo first, then when that didn't work I switched to root and tried it, this is the error:

bash: /dev/hdd1: Permission denied

what am I missing here?

ps: i copy and pasted the command from the above post.

EDIT: Next, I updated the uuid in the fstab to the uuid listed under 

ls /dev/disk/by-uuid -alh

the drive still doesn't appear to be mounted

/dev/hdc2 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=me)

?

---

### Post by bodhi.zazen on 2007-02-07
My last post is an entry for fstab, which is very similar to mount.

If you updated fstab, just use:

```
sudo mount /media/hdd1
```

If you did not update fstab, use mount:

```
sudo mount -t vfat /dev/hdd1 /media/hdd1 -o umask=000
```

---

### Post by Angry penguin on 2007-02-07
Good news. I can now mount the drive manually. How do I get it to automount on startup?

---

### Post by bodhi.zazen on 2007-02-07
You need to edit fstab.

In a terminal type : ```
gksudo gedit /etc/fstab
```

Try the entry in my previous post & reboot :

> /dev/hdd1 /media/hdd1 auto auto,nls=utf8,umask=007,gid=46 0 1

You may want to change to umask=000 (007 is more secure)

8)

---

### Post by Angry penguin on 2007-02-08
That didnt work. After I mount it manually, if I try to create a document in it, it says I don't have permission to write to the folder. Do I have to own the mount point before it will automount for my user?

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2 -- converted during upgrade to edgy
UUID=af0a308f-ae2b-43b9-a591-657ec13f881d / ext2 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=5A48602E48600B59 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdd1 -- converted during upgrade to edgy
UUID=45C3-5173 /dev/hdd1 /media/hdd1 vfat auto,nls=utf8,umask=000,gid=46 0 1
# /dev/hdc5 -- converted during upgrade to edgy
UUID=e068d356-ca33-419b-97f3-cdbdf975167f none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bodhi.zazen on 2007-02-08
You need to change this line:

UUID=45C3-5173 /dev/hdd1 /media/hdd1 vfat auto,nls=utf8,umask=000,gid=46 0 1

to

/dev/hdd1 /media/hdd1 vfat auto,nls=utf8,umask=000,gid=46 0 **0**

or 

UUID=45C3-5173 /media/hdd1 vfat auto,nls=utf8,umask=000,gid=46 0 **0**

But you can not use both UUID and /dev/hdd1 ...

EDIT: Missed that 1 at the very end. 1 should be used for your root partition only.

Use 2 if you want the file system checked at mount, but 0 (no check) should work as well.

You should change the other entries as well ;)

# /dev/hdc1 -- converted during upgrade to edgy
UUID=5A48602E48600B59 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 **0**
# /dev/hdd1 -- converted during upgrade to edgy
UUID=45C3-5173 /dev/hdd1 /media/hdd1 vfat auto,nls=utf8,umask=000,gid=46 0 **0**

---

### Post by Angry penguin on 2007-02-08
It still doesnt want to automount at startup

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2 -- converted during upgrade to edgy
UUID=af0a308f-ae2b-43b9-a591-657ec13f881d / ext2 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=5A48602E48600B59 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=45C3-5173 /media/hdd1 vfat auto,nls=utf8,umask=000,gid=46 0 0
# /dev/hdc5 -- converted during upgrade to edgy
UUID=e068d356-ca33-419b-97f3-cdbdf975167f none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

EDIT: found an error

 dmesg | tail
[   63.183540] Bluetooth: RFCOMM socket layer initialized
[   63.183556] Bluetooth: RFCOMM TTY layer initialized
[   63.183558] Bluetooth: RFCOMM ver 1.7
[   71.705887] cdrom: hda: mrw address space DMA selected
[   71.903742] cdrom: hda: mrw address space DMA selected
[   71.948781] ISO 9660 Extensions: Microsoft Joliet Level 3
[   72.063728] ISOFS: changing to secondary root
[   72.548896] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   72.778157] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  553.353508] FAT: Unrecognized mount option "nls=utf8" or missing value

not sure what its looking for...

---

### Post by bodhi.zazen on 2007-02-08
fstab looks ... nice :p

What command are you using to mount the partition after rebooting ?

Is the uuid correct ? Do you know how to check the uuid of a partition ?

you could try these options :

> /dev/hdd1 /media/hdd1 vfat defaults,nls=utf8,umask=000,gid=46 0 0
UUID=45C3-5173 /media/hdd1 vfat defaults,nls=utf8,umask=000,gid=46 0 0

Does anyone else see anything I am overlooking ?

---

### Post by Angry penguin on 2007-02-08
Alright, here's what I did. 

I copy/pasted the line from /etc/mtab for my thumbdrive (also formatted fat32), to the option line in /etc/fstab for hdd1.

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2 -- converted during upgrade to edgy
UUID=af0a308f-ae2b-43b9-a591-657ec13f881d / ext2 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=5A48602E48600B59 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=45C3-5173 /media/hdd1 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
# /dev/hdc5 -- converted during upgrade to edgy
UUID=e068d356-ca33-419b-97f3-cdbdf975167f none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

For whatever reason, it works. Read, Write, automount, everything. Now if someone could explain to me why in the hell this works and the previous one doesn't, I would really appreciate it.

thanks,

---

### Post by bodhi.zazen on 2007-02-08
8)

Since it is working, time to tweak ...

I have no idea why it is working, but you can always delete those options one at a time until it breaks and then check out the key option in man mount :twisted:

Edit :

Oh now I see your error message. The problem was nls=utf8

> Unrecognized mount option "nls=utf8"
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

The fix was changing to iocharset=utf8

---

### Post by Angry penguin on 2007-02-08
well, unless someone can give me a reason why I shouldn't leave it like this, I think I'm going to stop there. 

I've learned alot about fstab, I've learned that I never want anything to ever go wrong with it again!
thanks.

---

### Post by Angry penguin on 2007-02-08
> **bodhi.zazen said:**
> 8)

Since it is working, time to tweak ...

I have no idea why it is working, but you can always delete those options one at a time until it breaks and then check out the key option in man mount :twisted:

Edit :

Oh now I see your error message. The problem was nls=utf8



The fix was changing to iocharset=utf8

you are correct, I changed everything back to the way it was with the exception of the iocharset option and it works. w00t!

here is the final fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2 -- converted during upgrade to edgy
UUID=af0a308f-ae2b-43b9-a591-657ec13f881d / ext2 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=5A48602E48600B59 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=45C3-5173 /media/hdd1 vfat auto,iocharset=utf8,umask=000,gid=46 0 0
# /dev/hdc5 -- converted during upgrade to edgy
UUID=e068d356-ca33-419b-97f3-cdbdf975167f none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thank you for your help.

---

### Post by bodhi.zazen on 2007-02-08
> **Angry penguin said:**
> I changed everything back to the way it was with the exception of the iocharset option and it works. w00t!

Does this mean we can call you > Formally known as Angry Penguin:D

---

### Post by Angry penguin on 2007-02-08
The Geek Formerly Known as Angry Penguin. lol.

I will probably cease to be angry when I am completely free of the Microsoft stranglehold. It will happen as soon as I can get Counter Strike: Source running on Ubuntu. 

I had it working once but my issue was that I wanted the game to run at 1024x768 but my desktop to run at 1280x1024, that's where I got stuck. Different sessions maybe?

Oh, and my 5 button mouse wouldn't work inside the game even though I got it to work in Ubuntu (Nautilus and Firefox). That's a biggie. It's an mx500.

I also play Hitman and BF2.

But I would be happy if I could get CS:S working completely

---

