---
title: "About mounting drives at startup"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-06-06
Hi, I'm a complete Ubuntu newbie. I know aplenty about Windows and computers in general, but Ubuntu - its sorta weird. Here's my setup:

I have an 80 GB Drive, which runs Windows XP. I installed Ubuntu on a 10 GB drive. During installation, I used the second option there was, something like "use entire drive" or something. Since then, my Windows XP cannot identify the 10 GB drive. It seemingly appears in the Device Manager and Ubuntu runs fantastically, but in My Computers and such, it is missing.

Meanwhile, on Ubuntu, I need to mount the 80 GB everytime I startup, which gets annoying, because that's where all my documents and stuff are.Is there a beginner-friendly way to mount D: at startup? BTW, when in the "media" folder of Ubuntu, I can see all my removable drives and the 80gig drive, but I cannot access the 10gig drive, where Ubuntu is installed.

Where did I go wrong, and how to mount the 80gig drive at startup?

---

### Post by freebird54 on 2007-06-06
You could try reading my answer in this post  [http://ubuntuforums.org/showthread.php?t=465789](http://ubuntuforums.org/showthread.php?t=465789)
as it is about the same thing (more or less).  Should get you going.  If the drive is NTFS that you need to recognize, there will be a couple of changes to the mount line though.

In that case, there are other links given in the same thread that will help.

Enjoy!

---

### Post by Carlos Santiago on 2007-06-06
To help us helping you, place the content of the file /etc/fstab

---

### Post by steve.horsley on 2007-06-06
> I have an 80 GB Drive, which runs Windows XP. I installed Ubuntu on a 10 GB drive. During installation, I used the second option there was, something like "use entire drive" or something. Since then, my Windows XP cannot identify the 10 GB drive. It seemingly appears in the Device Manager and Ubuntu runs fantastically, but in My Computers and such, it is missing.
Microsoft choose not to allow Windows to recognise Linux filesystems, even though the specs are publlic knowledge. I think this is because MS don't want to make interoperability easy. There is a driver available for Windows that allows it to read ext2 file systems (free, open source of course), but I can't remember the name. Google should find some references for you.
> 
Meanwhile, on Ubuntu, I need to mount the 80 GB everytime I startup, which gets annoying, because that's where all my documents and stuff are.Is there a beginner-friendly way to mount D: at startup?
The instructions that freebird54 links to look good to me. Failing that, lookee here (and bookmark the guide anyway):
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions)

> BTW, when in the "media" folder of Ubuntu, I can see all my removable drives and the 80gig drive, but I cannot access the 10gig drive, where Ubuntu is installed.The 10 Gig drive contains your root ("/") file system. You are already on it. Fire up your file manager (by clicking Home for instance), click the Computer icon and double-click Filesystem. That's it there. Or open your home folder click Up until you can't go any further.

---

### Post by Sabretooth on 2007-06-07
> **steve.horsley said:**
> The 10 Gig drive contains your root ("/") file system. You are already on it. Fire up your file manager (by clicking Home for instance), click the Computer icon and double-click Filesystem. That's it there. Or open your home folder click Up until you can't go any further.

Hmm... That's what I was thinking. Ubuntu sure does take some time getting used to. :)

---

### Post by Inxsible on 2007-06-07
the driver to read and write to ext3 partitions from windows is called [FS Driver]("http://www.fs-driver.org")

---

### Post by Sabretooth on 2007-06-08
I tried freebird's suggestion, and it all goes well until the final "mount -a" line. Here I'm a message saying 

"mount: special device /dev/sda3 does not exist"

Here's my fstab thing: Not sure what the whole thing is supposed to mean and all, but there.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5ed3e8ec-ebaa-41f0-9752-299708d2afe3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=96e2b772-3de6-4018-85e5-ad5efa0f4e23 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda3  /media/disk    vfat    iocharset=utf8,umask=000  0    0

I'm thinking that changing the number in sda3 will help, but I'm not willing to take a risk.

---

### Post by Inxsible on 2007-06-08
Go to a terminal and post the output of the following command:
```
sudo fdisk -l
```
-l is a lowercase L. Make sure your disk is connected when you do this.

---

### Post by Sabretooth on 2007-06-08
Okay, sorry guys. I figured it out myself. I replaced the sda3 with hda1 and all is well now. Thanks a bunch, people!

---

