---
title: "How to: Mount External USB HD"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2007-05-28
After today's patch I have lost my Ext HD. I need to re-mount it, but have no idea how to do it.

Thanks,

Seth

---

### Post by taurus on 2007-05-28
If you need to reformat it, try using gparted (System -> Administration) to do that.  Don't mount it first or gparted won't format the drive.

And if you don't have gparted on your machine, install it with synaptic/apt-get/aptitude.

---

### Post by Sethalos on 2007-05-28
Oh no.  I don't want to reformat it. I have far too much on it to do that, lol.

I simply can't access it, it isn't showing up in my list of drives. So, I just assumed that I had to remount it so that it shows up.

Perhaps I'm wrong about that. Not sure how this all works yet.

Thanks,

Seth

---

### Post by taurus on 2007-05-28
Okay, you want to remount it.  I read a little too fast and though you wanted to reformat it.

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by GrueTamer on 2007-05-28
Give us the output of your /etc/fstab file please, with the information in there, I or somebody else can probably tell you what to do.

---

### Post by ruy_lopez on 2007-05-28
Plug the drive in. Run "fdisk -l". Look for the partition, probably under /dev/sda something. Then mount it like this:

```
sudo mount -t (fsys type) /dev/sda(whatever number) /media/mountpoint
```

If /media/mountpoint doesn't already exist, create it first, making sure you have permission to read and write.

If this works: add a line to fstab:

```
/dev/sda(whatever)  /media/mountpoint  (fstype) defaults 0 0
```

---

### Post by Sethalos on 2007-05-28
Ok, here is the terminal info asked for:

Disk /dev/hda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650       14588    55737517+   f  W95 Ext'd (LBA)
/dev/hda5            7650       14588    55737486    7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9588    77015578+  83  Linux
/dev/hdb2            9589        9964     3020220    5  Extended
/dev/hdb5            9589        9964     3020188+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

---

### Post by ruy_lopez on 2007-05-28
Looks like its /dev/sda1, the filesystem type is vfat, so to mount, use:
```

sudo mount -t vfat /dev/sda1 /media/mountpoint
```

---

### Post by taurus on 2007-05-28
```
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by Sethalos on 2007-05-28
> **ruy_lopez said:**
> Plug the drive in. Run "fdisk -l". Look for the partition, probably under /dev/sda something. Then mount it like this:

```
sudo mount -t (fsys type) /dev/sda(whatever number) /media/mountpoint
```

If /media/mountpoint doesn't already exist, create it first, making sure you have permission to read and write.

If this works: add a line to fstab:

```
/dev/sda(whatever)  /media/mountpoint  (fstype) defaults 0 0
```

I know this is going to be a stupid question, but where you have the (fsys type) I'm not sure what goes there.

---

### Post by ruy_lopez on 2007-05-28
for both mount and fstab, the fstype is "vfat", and instead of "defaults", use taurus's suggestion "iocharset=utf8,umask=000"

---

### Post by Sethalos on 2007-05-28
> **taurus said:**
> ```
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o iocharset=utf8,umask=000
df -h
```

First let me thank everyone for the help, this is what I love about the Linux community.

So, I entered all of this in my terminal, and it seemed to work fine.  Now when I navigate to Places - Computer, I still don't see the Drive Listed.

I also went to /media folder and looked for sda1, when I click on that, it shows up as containing 0 items.

So, probably my noobness is doing something wrong here.

Here is my printout again now that Ihave entered the above commands:

Disk /dev/hda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650       14588    55737517+   f  W95 Ext'd (LBA)
/dev/hda5            7650       14588    55737486    7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9588    77015578+  83  Linux
/dev/hdb2            9589        9964     3020220    5  Extended
/dev/hdb5            9589        9964     3020188+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

---

### Post by Sethalos on 2007-05-28
Sorry, this is the fstab file output as well.  

# /etc/fstab: static file system information.
#
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=3197a3b5-9214-474e-bd73-149077950a9b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=3de10065-e146-4022-8c35-0eab21bb5be6 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom2 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
# Generated by Automatix
/dev/sdc1   /media/sdc1   vfat    iocharset=utf8,umask=000  0    0
/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sda5   /media/sda5   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions

---

### Post by taurus on 2007-05-28
> **Sethalos said:**
> Sorry, this is the fstab file output as well.  

# /etc/fstab: static file system information.
#
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=3197a3b5-9214-474e-bd73-149077950a9b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=3de10065-e146-4022-8c35-0eab21bb5be6 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom2 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
[B][COLOR="Blue"]# Generated by Automatix
/dev/sdc1   /media/sdc1   vfat    iocharset=utf8,umask=000  0    0
/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sda5   /media/sda5   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions
[/COLOR][/B]

](*,)

---

### Post by Sethalos on 2007-05-28
Is there something highlighted that should not be there?  I understand the head to brick wall icon probably means something I've done isn't right, but assume I have no idea and let me know.

Thanks,

Seth

---

### Post by ruy_lopez on 2007-05-28
What does "df" say after you mounted /dev/sda1

---

### Post by taurus on 2007-05-28
Your /dev/sda1 is vfat, not ntfs.  And /dev/sdc is your CD drive (second drive) but you have /dev/sdc1 as vfat.  And there is no /dev/sda5.

---

### Post by Sethalos on 2007-05-28
> **taurus said:**
> Your /dev/sda1 is vfat, not ntfs.  And /dev/sdc is your CD drive (second drive) but you have /dev/sdc1 as vfat.  And there is no /dev/sda5.

Ok..so how do I change that so that it is proper?

Seth

---

### Post by Sethalos on 2007-05-28
Ok, so here's what I've done.

I typed in sudo nautilus, navigated to my /etc/fstab file and modified the line to read:

/dev/sda1   /media/sda1   vfat  iocharset=utf8,umask=000  0    0

Now the USB drive does show up in my drive list, but I'm getting an error that I don't have permissions to mount it.

Here is my new fstab file output:

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=3197a3b5-9214-474e-bd73-149077950a9b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=3de10065-e146-4022-8c35-0eab21bb5be6 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom2 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
# Generated by Automatix
/dev/sda1   /media/sda1   vfat  iocharset=utf8,umask=000  0    0
## End of Automatix mounted partitions

and my fdisk -l

Disk /dev/hda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650       14588    55737517+   f  W95 Ext'd (LBA)
/dev/hda5            7650       14588    55737486    7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9588    77015578+  83  Linux
/dev/hdb2            9589        9964     3020220    5  Extended
/dev/hdb5            9589        9964     3020188+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

I think I'm close now to getting this to work.

---

### Post by Sethalos on 2007-05-28
Ok, well at this point I'm totally lost. I think I have managed to screw up my CDROM drive listings and my Ext USB listing.

Not quite sure what I'm supposed to do now.

---

### Post by arnieboy on 2007-05-28
> **Sethalos said:**
> Ok, well at this point I'm totally lost. I think I have managed to screw up my CDROM drive listings and my Ext USB listing.

Not quite sure what I'm supposed to do now.

Let me take you ahead from here if you dont mind. 
please **unplug all your external USB drives** and post the following:
```
cat /etc/fstab
sudo fdisk -l 
```
I know you have done it before but do it again for a quick redressal.

-Arnie
Automatix Team Lead

---

### Post by fj4 on 2007-06-01
I don't mean to hijack the thread, but I have a relevant question.
I had to reformat my iAudio X5: FAT32, lba flag set... done.
Now how can I rename it and get it to mount in the same place it used to be in? I want it to mount as "IAUDIO" in /media. After formatting it just shows up as "disk." I might seem picky, but I want to know how so I can do the same for all my card readers and thumbdrives.
Thanks, any input is appreciated.

---

