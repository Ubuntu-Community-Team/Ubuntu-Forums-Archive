---
title: "How to format and mount new Sata drive"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-06-06
Hi guys,

I've just purchased a new 320gb Sata drive, and want to use it as a slave.

When I was installing Ubuntu Feisty on it, I tried to set it as a home partition, but I think I could only set home partition on a same physical disk (my ubuntu is installed on a 200gb hard disk).

Anyways, after booting, the sata 320gb disk wasn't mounted (nor was it formatted).

I wanted to ask how I could format it (to ext3) and mount it automatically every time?

Here is my fdisk:
```

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdb2            2551       24320   174867525    f  W95 Ext'd (LBA)
/dev/hdb3           24321       24321        8032+  83  Linux
/dev/hdb5            2551        5119    20635461   83  Linux
/dev/hdb6            5120        5250     1052226   82  Linux swap / Solaris
/dev/hdb7            5251       24320   153179743+  83  Linux

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
kinson@kinbuntu:~$ 

```

Much thanks in advance !

Cheers,
Kinson :)

---

### Post by Bachstelze on 2007-06-06
Use fdisk to create partitions on it, and then create a filesystem on the partition(s). You can also use GParted if you're scared of the command line.

---

### Post by LaRoza on 2007-06-06
To format it, use GParted. You can use it with Ubuntu or use a live cd. I would vote for the live cd, but it doesn't matter in this case. To have to mount on startup, I believe you would need to edit fstab, but I have never done that, hopefully, someone will fill in that gap.

---

### Post by Songwind on 2007-06-06
You can create and format partitions with gparted.  It's a very easy to use graphical tool in the system administration menu.

Once it is created and formatted you will want to add a line to fstab for it.  Rather than try to pull an fstab line out of my butt from work, I will suggest that you check /etc/fstab and model it on the line for /dev/hdb3.

The device for your new partition will probably be /dev/sda1 and instead of "/" you will want to mount it on /home.

PS, make a copy of your current /home directory before doing that, since it will become unavailable when the other file system is mounted on top of it.

---

### Post by kinson on 2007-06-07
Thanks :)

I've downloaded and installed gparted, and formatted the drive to a primary(whats the difference from extended?) ext3. Its a 320gb drive, but I only get 298gb as usual :(

I tried editing my fstab file, but I'm not too familiar with the UUID thingy is Feisty. Can anybody help me out here? I just ommited the UUID thingy, but I'm not sure whether it will affect anything. I'm quite worried of course, since its going to be the partition that'll be holding my data.

here's my fstab:```

kinson@kinbuntu:/media$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb5
UUID=560001fa-b126-4b3e-8322-ca1faf9a373e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb7
UUID=b82a6db4-c47c-49bd-b10b-d9faeb006c87 /home           ext3    defaults        0       2
# /dev/hdb1
UUID=88D4AF0AD4AEF998 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=d78a263e-ca00-4ed5-986b-7740eceb2f16 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/kinson   ext3    defaults        0       1
kinson@kinbuntu:/media$ 

```

I added the last line /dev/sda1 and tried to mount it on /media/kinson. 

I think it worked, cause after that I could access the files from /media/kinson.

The funny thing is though, even though its a 320gb, and I only get 298gb, but when I check the file size, it now says 278gb(even less!!)?

here's my disks:
```

kinson@kinbuntu:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb5              20G  2.3G   17G  13% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  108K  506M   1% /proc/bus/usb
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/hdb7             144G  252M  137G   1% /home
/dev/hdb1              20G  4.3G   16G  22% /media/hdb1
/dev/sda1             294G  191M  279G   1% /media/kinson
kinson@kinbuntu:/media$ 

```

I don't know what the 191MB is used for. But even then, I'm missing about 15GB. Which is really confusing :(

Hoping you guys can help me out here :D

Cheers,
Kinson

---

### Post by Songwind on 2007-06-07
A few things are at work here.

a) drive manufacturers generally label and market their product on the premise that 1Gb = 1000Mb.  This is not the case.  Most Linux software is going to do the actual conversion of 1024Mb, and that 1Mb = 1024kb, etc.  So if Maxtor or whoever is saying a drive is 320,000,000,000 bytes, that's actually 298Gb.

b)  Part of your drive is taken up for file tables and partition table and such.  So of the 298Gb you have, some is in use that way.  WHich is probably where the 294Gb formatted size.

As for why 294 - .191 = 279?  I've got nothin'.  I haven't had that issue yet.

---

### Post by kinson on 2007-06-07
Thanks for the speedy response :)

I understand point a, and I understand point b too. But like you said...its till weird to lose 15gigs like that, on a newly formatted drive :/ If it were 1gig or so I wouldn't bother too much...but 15gigs is a lot :p

Another thing though. Though I've added the new drive to my fstab(I haven't rebooted my pc though). It doesn't show up in the nautilus list of files. I can only manually drag it down to the list, below my usual drives. I've attached a screenshot here:

[http://img501.imageshack.us/img501/9953/screenshoths3.png]("http://img501.imageshack.us/img501/9953/screenshoths3.png")

Cheers,
Kinson

---

