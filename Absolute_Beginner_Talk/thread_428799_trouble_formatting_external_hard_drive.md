---
title: "trouble formatting external hard drive"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Rob2Kx on 2007-04-30
Hi,

I have an external hard drive that is currently NTFS formatted (I just switched from Win xp).

I'd like to format it to ext3.  I'm using gparted.  Here's the problem:

In gparted when I select the drive I want to format from the pull down menu on the right side, there is an orange exclamation point sign beside the partition name.  When I right click on the partition for information, there is a warning that states:

statvfs (/media/Maxtor External\040Drive):
No such file or directory

So as a result of that, I can't select any options from the partition menu.
I feel like the \040Drive part shouldn't be there.

Any ideas?

Thanks in advance.

---

### Post by bobbybobington on 2007-04-30
If all else fails, you could try formating it as fat32 fs from a windows machine. perhaps fat32 would make more sense cause it's cross platform. Sorry I don't have a more a more direct answer to your problem :(

---

### Post by GrueTamer on 2007-04-30
I'm just throwing this idea around, but you could try cfdisk (type cfdisk in the terminal, followed by the drive, aka /dev/<whatever>).  Even though limited in features compared to gparted, it's been more reliable to me than anything else, so I recommend it.

---

### Post by Rob2Kx on 2007-05-01
> **GrueTamer said:**
> I'm just throwing this idea around, but you could try cfdisk (type cfdisk in the terminal, followed by the drive, aka /dev/<whatever>).  Even though limited in features compared to gparted, it's been more reliable to me than anything else, so I recommend it.

k, I tried that and here's what I got back:

FATAL ERROR: Bad primary partition 0: Partition ends after end-of-disk

---

### Post by Rob2Kx on 2007-05-01
So I guess it's looking like I'm screwed here... So last question:

If I keep my external hard drive as NTFS, and keep using it as normal, will that cause issues with Ubuntu down the road?

---

### Post by Inxsible on 2007-05-01
No you are not screwed..........yet !!
 
I came across this very problem -- for one of my partitions on the internal drive.
 
This is what I did. You will need GParted from the LiveCD. The installed version will **NOT** do !
 
Put in your LiveCD and start GParted. It will show you all the drives and partitions that you have. On your external HDD you will "probably" see a lock icon or an exclamation mark. 
 
This tells you that it is mounted in another OS. A mounted drive cannot be partitioned/formatted. So right click and unmount the drive and then go ahead with the format.
 
Note: Make sure you back everything up on that drive before doing this. You must already be doing this since you are formatting it. But just wanted to caution you.

---

### Post by qpieus on 2007-05-01
Is the drive mounted when you're using gparted? Or are you using gparted while logged into ubuntu? You wrote that you see the message:
statvfs (/media/Maxtor External\040Drive)

the "/media" path makes it sound like the drive is mounted. Try out the gparted live cd at:[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") if you haven't already tried it.

I had a similar problem where gparted (running within ubuntu) could not format an external drive. But the gparted live cd worked perfectly to reformat my drive (to ext3).

To answer your question regarding future problems if you leave the drive as is - sure, problems could be likely. The errors you're getting may mean there's some problem with the existing partition or drive, so you may have problems with whatever OS you use with the drive. I agree, you definitely need to reformat that baby.

Another thought is to use a maxtor/seagate disk utility program (if any exist - they probably do) to diagnose and/or fix whatever problem the disk has. Maybe they have a formatting utility also....

---

### Post by Rob2Kx on 2007-05-01
Inxsible and qpieus:

I tried booting ubuntu off the Install CD.  And I still encountered the same problem, BUT here's what I found out.  I tried to unmount the drive in gparted but got an error saying that it couldn't be unmounted

umount: /media/Maxtor External\040Drive: not found

I checked the properties of the drive by right clicking on the desktop icon, and under the volume tab it says that the drive is mounted as /media/Maxtor External Drive

So, gparted says it is mounted as /media/Maxtor External\040Drive while the volume information shows it being mounted as /media/Maxtor External Drive

Maybe the file name is too long (ie: Maxtor External Drive)?  or the \040 just shouldn't be there in gparted?  Is there any way I can reconcile the two mount points?  Or is there not even a problem there?

Thanks... I feel like we're at least making headway.

Edit:  For what it's worth I also have another external drive, and it has the exact same problem - Different manufacturer and all.

---

### Post by qpieus on 2007-05-01
I'm confident the gparted live cd will work for you. So far, the drive has been mounted when you've been trying to format it. And it looks like maybe the spaces in the volume name are causing problems too. With the gparted live cd, you boot your PC off that cd and NO drives will be mounted. Then gparted should work properly to reformat your external drive. Be careful when using gparted so that you select the correct drive to perform the operations on - it's easy to select the wrong drive in the gparted interface (if I remember right, you select the drive from a drop down box).

---

### Post by bobplano on 2007-05-01
> **qpieus said:**
> And it looks like maybe the spaces in the volume name are causing problems too. 

yes i'm pretty sure those spaces aren't helping any. linux doesn't like spaces as i've learned from personal experience

---

### Post by antoz on 2007-05-01
I think Ubuntu (including the live CD) mounts all external drives by default. Maybe try to "umount" it from the terminal or get the Gparted live CD I am sure that would be able to format the drive.

---

### Post by Rob2Kx on 2007-05-02
Hi again!  Thanks for the help from everyone.

I did it.  I managed to do it by booting off the CD and changing the mount location to something real simple (just to make sure)... got a few error messages... but in the end it worked.

Anyways, its sorted!  phewf.  Now how can I give myself write access to the drive??? ha

---

### Post by qpieus on 2007-05-02
> **Rob2Kx said:**
> Hi again!  Thanks for the help from everyone.

I did it.  I managed to do it by booting off the CD and changing the mount location to something real simple (just to make sure)... got a few error messages... but in the end it worked.

Anyways, its sorted!  phewf.  Now how can I give myself write access to the drive??? ha
Good job, congrats.
As far as write access goes, you need to install/setup a driver called ntfs-3g. What version of ubuntu are you using? In feisty, ntfs-3g is enabled by default (I think - I haven't installed feisty yet). In the older versions of ubuntu you need to install and setup ntfs-3g because it doesn't come by default. There are tons of threads in the forums about write access to ntfs partitions. Search for "ntfs-3g" and you'll get a lot of hits. 
Here's the main thread for the ntfs-3g driver (it's really big though, you can't read the whole thing unless you have unlimited time to do so):
[http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by rcmullins on 2007-05-08
I am having the same problem with trying to re-format an external hard-drive.  I tried the cdisk, and had the same error 'extends beyond end of partition'.

I downloaded the ISO and copied it to the disk, but cannot figure out how to fire it up.  When I slide the CD in, Ubuntu opens the disk like a file folder instead of running.

Any thoughts?

---

### Post by Inxsible on 2007-05-08
Did you burn the CD as an ISO image, or  just plain Data CD. you have to burn it as an iso image to have it autorun the Ubuntu Live CD

---

### Post by rcmullins on 2007-05-08
I must have burned as a data, do I have to install anything new to burn ISO's or will the default Ubuntu Feisty build have something on it that will do that?

All I see on the system is audio creators, and music cd extractors.

Thanks.

---

### Post by Inxsible on 2007-05-08
> **rcmullins said:**
> I must have burned as a data, do I have to install anything new to burn ISO's or will the default Ubuntu Feisty build have something on it that will do that?
 
All I see on the system is audio creators, and music cd extractors.
 
Thanks.
 
I am sorry, but I am a bit confused. You already have Ubuntu installed? In that case why are you burning the Live CD now ?

---

### Post by rcmullins on 2007-05-08
I am due to some problems with an external hard-drive formatted with NTFS, I have recovered the files I want but now only mounts as read only.  There are some bad files on the hard-drive, and since I can only mount in 'read-only' I cannot get rid of them or make changes to the hard-drive itself;
/dev/sdb1

It is a Western Digital, so I figured the best way to fix this is to save all the files I could, and simply reformat the drive to Fat32 or something similar, so I could continue using the drive.

Here is the thread to my problem if you have alot of time to kill. ;)
[http://ubuntuforums.org/showthread.php?t=419692&page=2](http://ubuntuforums.org/showthread.php?t=419692&page=2)

Thanks very much for your help.

---

### Post by ronb on 2007-05-09
> **rcmullins said:**
> I must have burned as a data, do I have to install anything new to burn ISO's or will the default Ubuntu Feisty build have something on it that will do that?

All I see on the system is audio creators, and music cd extractors.

Thanks.

Insert a blank CD  and right-click on the ISO image from Nautilus. You'll get an option to **Write to Disc...**

This will burn the image to the disc instead of the file.

---

