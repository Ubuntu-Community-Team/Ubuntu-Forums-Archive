---
title: "One Feisty Hard Drive"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Dev0205 on 2007-05-27
Dear Linux Community,

I've got a second Hard Drive that is driving me absolutely crazy. I just want to use this drive as a backup that can work between Linux and a future Windows partition &#8220;For gaming&#8221;. I was able to finally modify the files on the drive after downloading NTFS-3G, but only by forcing the mount in the terminal. I read that formating the drive to Fat32 would give me the best of both worlds, so I did that with Gnome Partition Editor. Not shortly after, the drive will no longer let me mount it. Here are the errors I am getting;

1.When trying to mount from inside Nautilus I get &#8220;Cannot mount volume. You are not privileged to mount this volume.&#8221;
2.When trying to mount from the Terminal as Root I get &#8220;mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
 missing codepage or other error
. In some cases useful info is found in syslog &#8211; try
 dmesg | tail  or so
.

Have I corrupted the partition or damaged the drive? I'm not worried about the data on it &#8220;I made a backup prior to converting it from NTFS to FAT32&#8221;. 

I would love to be able to use this drive again and appreciate your support. I'm new to Linux and not quite up to speed with the lingo.

Cheers,
Dev0205

---

### Post by confused57 on 2007-05-27
Here's a couple of links for mounting Window's partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Dev0205 on 2007-05-27
Confused57,

I'll give those links a shot. Do you think I would be able to access the drive if I made it EXT? Right now I'd just like to have it so I can tinker with Ubuntu and not worry about losing data.

I'd basically like to know how to format the drive or scan it for errors..and then get back to saving data on it. Thanks for the quick reply.

---

### Post by ryanVickers on 2007-05-27
I would make it EXT3 just for the piece of mind that it's not a microsoft partition!  Fat32 especially is very prone to corruption.  When you wnat to back up your windows, just use ubuntu to view the windows data and copy it to the ext3.

---

### Post by confused57 on 2007-05-27
> **Dev0205 said:**
> Confused57,

I'll give those links a shot. Do you think I would be able to access the drive if I made it EXT? Right now I'd just like to have it so I can tinker with Ubuntu and not worry about losing data.

I'd basically like to know how to format the drive or scan it for errors..and then get back to saving data on it. Thanks for the quick reply.

Formatting the drive as ext3 filesystem might be a good choice...when you install Window's, there's a program that enables Windows to read/write to ext3:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

An excellent partitioning utility is the gparted live cd(45 Mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

The links I gave you in my other reply also have methods to mount ext3 partitions.

---

### Post by Dev0205 on 2007-05-27
EXT3 Is looking like the way I'll end up going. I'm very new to the way things work in the Terminal. I'm ready to format the drive but this stuff about editing my "/etc/fstab" really confuses me. The last time I edited something, I had to reinstall Ubuntu lol. By the way, what is /ect/fstab anywho? Just a file that keeps tracks of drives and mounting?

I feel like were getting somewhere with it.

---

### Post by ryanVickers on 2007-05-27
I would agree to use gparted instead of terminal.  You also can add it (GNOME partition editor) on to ubuntu, so you don't have to boot from  the disk every time you need to change something.  Only use it when you're modifying your main partitions or something won't unmount properly.

---

### Post by Dev0205 on 2007-05-27
I'm formatting the drive like crazy but still having mount problems. I'll crack at it a bit and see what comes up.

---

### Post by ryanVickers on 2007-05-27
are you just waiting or telling it to mount.  just a though, sometimes they don't auto-mount.  But if it still doesn't work after like 3 re-formats, then I would say it's probably a hardware incompatibility problem, or maybe a failure, but more likely just incompatible.  also, I have an external drive, and every now and then, it locks up and I have to unmount then unplug it and plug it back in and then it works again for like another half hour.  really annoying when your doing large transfers!

you know what else is really annoying, when you tell it to unmount something (but not like a cd) and it does, but then realizes it's attached and mounts it again in like 2 seconds!  Just another problem I have with my external drive.  I have to click unmount, then quickly unplug it before it onnects again, it's kind of funny! :lolflag:

---

### Post by Dev0205 on 2007-05-27
RyanVickers,

Yup. It's another internal drive that I am just trying to Format to EXT3..and mount it in Ubuntu. The formatting in Gparted is working with no problem but the mounting after is. Gparted shows the drive as 

Partition              Filesystem               Mountpoint
/dev/hdb1           ext3                          /media/Media

When I go to mount the drive in Ubuntu via Nautilus I get 
"You are not privileged to mount this volume."

When I try to mount the freshly formated drive as root via the Terminal I get root@devin-desktop:/home/devin# mount /dev/hdb1
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Am I typing something wrong? I tried fdisk -l and got this :
root@devin-desktop:/home/devin# fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7297    58613121   83  Linux


Leave it to me being a complete newbie to make something this simple complicated. Does this information clear anything up?
P/S- /dev/hdb1 is the drive I'm trying to get to work correctly.

---

### Post by Dev0205 on 2007-05-27
While hanging around I choose to mount the drive via Gparted and it showed up on my desktop. However, I'm still not having any luck with the permissions. :(

---

### Post by rillip on 2007-05-27
try this:

sudo mount -t [filesystem type] /dev/hdb1 /mnt/yourdirectory

Where filesystem type is ext3, vfat, ntfs, etc. whatever you have it formated as now.  yourdirectory is where you want the directory mounted at in the file system.  I put mine in /mnt/storage

---

### Post by freebird54 on 2007-05-27
What may not have been explained is that you need to create a directory (his example is /mnt/storage) a place holder for the drive until it is mounted. Once you HAVE mounted it, going to /mnt/storage will take you to your drive.  If you use /mnt as your mount point, the drive will be there in Nautilus, but not on the Desktop.  If you mount it into /media  (ie: /media/storage) then it will default to showing up on your Desktop in the same way that CD's do when you have something in them...

Hope this helps!

---

### Post by Dev0205 on 2007-05-27
Freebird54,

I think I understand what you are talking about. I believe my current mount point is /media/Media. However, I have been unable to mount the drive by any means other than right clicking it while in gparted and saying mount on /media/Media. I have a feeling the issue is something really simple that I'm over looking? I really do appreciate the help.

---

### Post by freebird54 on 2007-05-27
Here is a typical 'added' line for /etc/fstab and an ext3 partition.  If you put something similar to this in the file, (with the bold part corrected if necesary to match your actual drive/partition number) you should be fine.
```

sudo cp /etc/fstab /etc/fstab.backup_070527
gksudo gedit /etc/fstab
```

and just add this line at the bottom

```
/dev/**hdb1**     /media/MEDIA           ext3    defaults        0       2
```

This assumes that the directory /media/MEDIA exists, and is empty before you try this!  Once you have saved and exited, try:

```
mount -a
```

to have it check for new things and mount them.

All the other stuff (UUID number etc) are nice in some cases - but not required just to get it going.  Hope this helps!

---

### Post by confused57 on 2007-05-27
You're in good hands with freebird54, but this psychocat's section may help:
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by Dev0205 on 2007-05-27
Freebird54,

Thanks for laying that out for me. It looks like fstab was still using the old settings for the drive "When it was ntfs". I made the changes you suggested and am now able to mount/umount the drive as root. I'd like now to be able to mount the drive as a normal user and create/modify files as I wish.  In the link confused57 sent me "http://psychocats.net/ubuntu/mountlinux" it says to:

sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage

As a means to set something like that up. Do I just change it like this?

sudo chown -R devin:devin /media/Media
sudo chmod -R 755 /media/Media

Forgive me for the 1000 questions. I'm honestly learning something new every time one of you says something.

---

### Post by freebird54 on 2007-05-27
If it needs a change - that should do it.  If the entry is in the /etc/fstab file, it should be automounted every time you login. the 'defaults' entry on the line I gave you should ensure that your settings remain each time. 

```
man mount
```

will give you far more information than you are ever likely to use/need.  You might want to check umask, user and a couple of other options though  :)

---

### Post by Dev0205 on 2007-05-27
Freebird54

sudo chown -R devin:devin /media/Media
sudo chmod -R 755 /media/Media

didn't seem to change anything. I'm not quite sure I understood you about the "man mount" part. I'm willing to bet I didn't add the correct code to my fstab. Here my current fstab:

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=c57fcd19-5b8c-47b3-abc0-547fb439d619 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=581d2451-f944-4620-95cb-fc27a81876e1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/Media ext3 defaults 0 2

Am I mising something from /dev/hdb1 to give me read/write access 24/7 to that drive? 

I'm spamming the refresh button here :D

---

### Post by confused57 on 2007-05-27
Did you happen to?:
```
sudo mkdir /media/Media
```

Ubuntu is case sensitive, so it would have to be exactly as you have it in your fstab.

---

### Post by Dev0205 on 2007-05-27
I'm pretty sure the directory already exists. I checked the terminal by typing sudo mkdir /media/Media and got:

mkdir: cannot create directory `/media/Media': File exists

---

### Post by confused57 on 2007-05-27
You might want to open a terminal & check the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Also, since you're using Feisty, you might want to mount your ext3 partition, using UUID's:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

You already have a directory for a mountpoint, but the link is pretty easy to follow.

---

### Post by Dev0205 on 2007-05-27
Confused57,
Here is the results of my fdisk -l. 

>  devin@devin-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7297    58613121   83  Linux


The UUID's are a bit confusing to me but I'll give that link a long read. I was hoping I would not have to get into those to set up the permissions.

While typing blkid I got :

> /dev/hda1: UUID="c57fcd19-5b8c-47b3-abc0-547fb439d619" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="581d2451-f944-4620-95cb-fc27a81876e1" 
/dev/hdb1: TYPE="ntfs" 

I wonder why my drive is still showing up as ntfs??

---

### Post by confused57 on 2007-05-27
It just dawned on me, better late than never, but I'll bet Feisty recognizes your drive as /dev/sdb..."sudo fdisk -l" will show this.

Added:  Just saw your last reply, it's indeed /dev/hdb...using UUID's is really quite easy...once you get the UUID from "blkid", you can just copy & paste it into your /etc/fstab entry, as described in the link.  The permissions are already set in fstab, using the method on Herman's website.   Using UUID's, it doesn't really matter if it's hda or sda.

Just saw your edit of your blkid results...what does gparted show?   You can use the gparted live cd to do a filesystem check:
> When you are using GParted -- LiveCD , you can initiate a filesystem check by right-clicking a partition, and selecting 'check' from the right-click menu, then click 'Apply'.
When the operation is finished you should click the '> Details' and then the 'Check and Repair' line, which expands into three subsequent lines.
These are, 'calibrate', 'check filesystem for errors and (if possible) fix them', and 'grow filesystem to fill partition'.
When you click on each of these you get more details of what has been done.
The middle line, 'check filesystem for errors and (if possible) fix them', when clicked, tells you the command GParted LiveCD used for the check, and when you click on the line describing the command, it expands into a full report on the state of your filesystem, which is super cool!
Thanks plors and the team at GParted LiveCD!
The above quoted from Herman's website.

This has more than likely been the cause of your mount problem.  I don't know if reformatting with the gparted live cd would help or not.

---

### Post by freebird54 on 2007-05-27
You can see the difference when you use the UUID info instead of the /dev/hdb1 reference by looking in your existing /etc/fstab file.  The advantage to using the UUID is that it doesn't change if the order and number of the drives happens to change (you plug it in differently, or add an external or...).  If you don't expect that to happen, you don't NEED the UUID method.

On the off-chance you want it though (for consistency maybe?) use:

```
sudo vol_id -u /dev/hdb1
```

and copy/paste the output to where you need it....

Are you still having troubles?  What are the errors you are getting if so?

---

### Post by confused57 on 2007-05-27
> I wonder why my drive is still showing up as ntfs??
Do you think it's possible that the drive was mounted when you tried to format?  I've never tried it before, so I don't know if you'd get error messages by doing this...at least with gparted live cd, the drive wouldn't be mounted.

---

### Post by Dev0205 on 2007-05-27
I feel like we are near some conclusion. I was able to pull my drives ID up but am seriously confused on where to place it in the fstab. I'm sure you understand, the majority I see all looks Greek to me.

Here is my current Fstab: 
> # /etc/fstab: static file system information.
#
# -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=c57fcd19-5b8c-47b3-abc0-547fb439d619 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=581d2451-f944-4620-95cb-fc27a81876e1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/Media ext3 defaults 0 2

Now I just need to add my drive ID     563915ef-8ff1-456d-b529-ea5537fb9080

Do I just add something like
# Entry for /dev/hdb1
UUID=563915ef-8ff1-456d-b529-ea5537fb9080 /ect3 defaults, 0 2   ? 

Once again, thank you both for your support. I've been dealing with this hard drive issue for the past week or so. I've learned a lot today/night. :D

---

### Post by freebird54 on 2007-05-27
Your entry should read


```
# Entry for /dev/hdb1
UUID=563915ef-8ff1-456d-b529-ea5537fb9080 /media/Media ext3 defaults  0  2
```

if the partition *IS* formatted ext3  (which it seems to be from the fdisk -l command)
I don't see any sign of an NTFS listing there - so what problem are you actually having?
Are you sure that when you were working with it in GPartEd that you formatted it after specifying it as ext3?  (check mark in the box under the format heading).

Everything else looks right to me.

---

### Post by confused57 on 2007-05-27
> **Dev0205 said:**
> I feel like we are near some conclusion. I was able to pull my drives ID up but am seriously confused on where to place it in the fstab. I'm sure you understand, the majority I see all looks Greek to me.

Here is my current Fstab: 


Now I just need to add my drive ID     563915ef-8ff1-456d-b529-ea5537fb9080

Do I just add something like
# Entry for /dev/hdb1
UUID=563915ef-8ff1-456d-b529-ea5537fb9080 /ect3 defaults, 0 2   ? 

Once again, thank you both for your support. I've been dealing with this hard drive issue for the past week or so. I've learned a lot today/night. :D

You might want to use an entry similar to the one in Herman's link:
```
#/dev/hdb1       
UUID=563915ef-8ff1-456d-b529-ea5537fb9080  /media/Media  ext3  rw,user  0    1
```

if the one freebird54 doesn't work.

---

### Post by Dev0205 on 2007-05-27
The problem I am having is that the permissions for the drive seem to be messed up. The only way I can mount the drive is by using the sudo command in the termnial. Even then I can only copy files to the drive. No creating folders or deleting them.

I've been trying to find a way to set the permissions up so that I can just access the drive from Nautilus "as a normal user that has to enter a password when trying to mount". And I'd like to have read/write/delete options. I hope I'm making sense here.

I understand you guys may be at the ends of your ropes as well. I may just try to backup my data and reinstall ubuntu?

---

