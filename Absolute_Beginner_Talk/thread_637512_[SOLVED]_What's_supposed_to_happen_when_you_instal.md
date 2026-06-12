---
title: "[SOLVED] What's supposed to happen when you install a new internal HDD?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-12-11
Hi, please excuse the utterly noobish question.

I just put a new Seagate Barracuda internal HDD to my Everex gPC. I plugged in the power and data cables, and rebooted.

What's supposed to happen? Is it supposed to automatically mount? If so where? I can't really tell if I installed it right, but I could just be looking in the wrong place.

If this is supposed to be blindingly obvious, then I'm either completely missing something, I didnt' install it right, or there's an incompatibility. Just trying to figure out which!!

Thanks

---

### Post by rockinlinux on 2007-12-11
your running ubuntu on the gpc? how is it working? 

ok now for your question.....

if i understand you right you put in a second HD right? is it IDE or SATA?

---

### Post by Thanoulis on 2007-12-11
You should be able to mount your second drive from nautilus...
As for the auto-mount you'll have to edit /etc/fstab.

---

### Post by ResumeMan on 2007-12-11
> **rockinlinux said:**
> your running ubuntu on the gpc? how is it working? 

Well it's the installed gOS, which is just Ubuntu w/the customized Enlightenment desktop. Works fine, not the fastest computer but good enough (I'm setting it up as a file server, hence the added drive). I'm mostly using the command line and Webmin, and VNC'ing into it occasionally as needed. Once everything is running the way I want I may disable the GUI, but I still lean on it sometimes.

> **rockinlinux said:**
> ok now for your question.....

if i understand you right you put in a second HD right? is it IDE or SATA?

D'oh! Talk about leaving out the most basic information :oops:  It's a SATA drive. The MoBo has 2 SATA ports on it. And ya, it's a second drive, intended to be used for data storage and file serving.

After I posted it occurred to me that I never tried going into the BIOS to see if I needed to tweak anything; is that a place to start? 

Thanks

---

### Post by rockinlinux on 2007-12-11
i think maybe, im not totally sure but you should be able to see the drive in the /dev folder.

---

### Post by rockinlinux on 2007-12-11
yes i would say thats a place to start if it not in the /dev.

i have been thinking about getting a couple gpcs for webservers and file servers....i can wait for you to tell me how it all works out!! :) what a good deal....200 bones....thats a great price. I think though i would try to put ubuntu server on there....maybe.

---

### Post by rockinlinux on 2007-12-11
oh yeah...just to be sure...

you did plug int the two cable right? im sure you did but just making sure...there should be a power plug and a data plug....

---

### Post by kpkeerthi on 2007-12-11
Verify if your new hard disk partition is listed by running in terminal
```

sudo fdisk -l

```

Follow[ this thread]("http://ubuntuforums.org/showpost.php?p=3907715&postcount=3") to help you format and mount it at startup. 

**Note:**
1. Choose ext3 for Filesystem option in gparted
2. Assuming /dev/sdb as your new HDD, your fstab entry should look like
```

/dev/sdb         /media/DATA               ext3        defaults

```

---

### Post by skymera on 2007-12-11
is it formatted?

maybe its not formatted and cant mount as there is no filesystem?

---

### Post by rockinlinux on 2007-12-11
ahhh!! i cant believe i didnt catch that! no its not formatted because he just put it in...

and 

the fdisk....that is nothing but genius and common sense  LOL :)

it must be a slow day for me ;)

---

### Post by skymera on 2007-12-11
so once he formats its able to mount.

i rule :)

---

### Post by rockinlinux on 2007-12-11
so yeah anyways....

you need to run the ```
sudo fdisk -l
```

it should show your new drive.

then use gparted (in ubuntu or the garted disk) and format the drive. i would format it to ext3 unless you are going to have windows coputers using it then do it to fat32 or if the gos has NTFS support format it to NTFS. EXT3 is the best because it almost does not fragments at all. If you have windows machines you could also install the ext3 driver so they could access the ext3 partition.

after you format it reboot (or if you used a gparted disk boot) your machine. look in the /dev folder and it should be there. to get it to auto mount edit you fstab.

---

### Post by rockinlinux on 2007-12-11
> **skymera said:**
> so once he formats its able to mount.

i rule :)

yes , yes, for today you are the one, the man, you rule and rock ;) :):guitar::lolflag:

---

### Post by ResumeMan on 2007-12-11
Hehe, funny thread :) You do rule indeed :-D

Yup the fdisk -l is the answer I wanted, I just didn't know it ;)

fdisk found it no problem. I need to run to work now, but I'll play with this when I get home, and I assume it will work no problem. Looks like it's currently formatted in FAT32, but I'll change that to ext3.

I knew it was likely to be simple, just didn't know where to go with it -- and my initial searches didn't turn anything up.

Thanks all!

---

### Post by ResumeMan on 2007-12-11
If you wouldn't mind I'd like some assistance in ensuring I'm interpreting the fdisk output correctly.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb8ccb8c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9566    76838863+  83  Linux
/dev/hda2            9567        9729     1309297+   5  Extended
/dev/hda5            9567        9729     1309266   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae827c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)
```

etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e4ab2464-38bb-4820-aa67-d1d65f36666b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b3d4e797-a9b5-45b3-8192-672d2001e08c none            swap    sw              0       0
##/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1  /media/6853-5BA9  vfat  uid=1000,gid=1000,exec,nodev,umask=003  0  0
```

Here's what is connected to my computer:

The original IDE 80 GB drive with the OS installed -- obviously hda
A 500-GB external USB drive, which is mounted. This presumably is sda1
The new 500-GB internal SATA drive. I would have to assume that thats' sda right? It says it's 500GB and doesn't have a valid partition table (i.e. isn't formatted).

Seems pretty straightforward (and of course I could try unplugging th USB drive too) but I wanted to proceed cautiously to make sure I don't delete all the files on the external!!!

Thanks a lot.

---

### Post by kpkeerthi on 2007-12-12
Just disconnect your external drive until you setup your new HDD.

---

### Post by shadow-of-sin on 2007-12-12
As shown in your fdisk output, your external USB HD is sdb1:
> /dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)

Don't rely on the fstab contents if you installed a new hard drive as it isn't updated automatically (you'll have to do it manually afterwards).

But yeah, as kpkeerthi said you should disconnect your external HD just in case.

---

### Post by ResumeMan on 2007-12-15
Worked like a charm, thanks!

Incidentally, when I put in the disklabel, I left it the default, which was "msdos." Is that the optimal label to use or should I select one of the others from the drop-down?

---

### Post by pelago on 2007-12-16
I think 'msdos' is the right disklabel. At least, all my Ubuntu systems, setup using the Ubuntu installer, use 'msdos' as the disklabel, so I figure that if it's good enough for the Ubuntu installer, then it should be good enough for manually setup drives.

I too am just adding a new HDD to an existing Ubuntu system. I have the drive formatted using gparted and I'm just about to edit fstab. Is there an automatic or GUI way of modifying fstab, or does it have to be by hand? Also, I notice my existing fstab, setup by the Ubuntu 7.04 installer, has entries like:

UUID=7ce612c8-cd6e-4f32-86fc-61a8842d3b41 /               ext3    defaults,errors=remount-ro 0       1

How do I get the UUID of the new drive/partition so I can use that instead of hardcoding /dev/sdb1? I assume there is an advantage of UUIDs - can anyone point to an explanation of why the Ubuntu installer uses UUIDs rather than /dev/sda1-type entries?

---

### Post by pelago on 2007-12-16
Answering my own question, I've found [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID) which explains why to use UUIDs (because they don't change from boot to boot) and says how to find out the UUID.

---

