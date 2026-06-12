---
title: "file retrieval"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by rjolley on 2006-09-03
I had a very important homework file stored on linux before the last update that broke my interface, I don't have time to bash my head against the wall, instead I tried a few fixes, they didn't work, so I reinstalled ubuntu on a seperate partition.  I can access my old partition but I can't figure out where the file is located.  I saved it in a directory called "school\cs5340" in the default folder when you start terminal.  How can I get back to this spot? 
Thanks for your help
Rex

---

### Post by xXx 0wn3d xXx on 2006-09-03
> **rjolley said:**
> I had a very important homework file stored on linux before the last update that broke my interface, I don't have time to bash my head against the wall, instead I tried a few fixes, they didn't work, so I reinstalled ubuntu on a seperate partition.  I can access my old partition but I can't figure out where the file is located.  I saved it in a directory called "school\cs5340" in the default folder when you start terminal.  How can I get back to this spot? 
Thanks for your help
Rex
Look in /home/$USER/school/cs534 in you old partition.
 
if it is not there cd into the partition and in terminal type:

whereis name.of.file

---

### Post by aysiu on 2006-09-03
Get a Knoppix CD. Those are always great to have around--much easier to use Knoppix to recover a file than to reinstall Ubuntu.

---

### Post by rjolley on 2006-09-03
My mistake, as it turns out I can't access the old partition, when i click on it in the file browser it says:

Unable to mount the selected volume.

error: device /dev/hda1 is not removable

error: could not execute pmount

it has previously done this will all of my non-linux partitions, but I figured that was because they were ntfs, I guess I was wrong about that.
Further thoughts?

Rex

---

### Post by xXx 0wn3d xXx on 2006-09-03
> **rjolley said:**
> My mistake, as it turns out I can't access the old partition, when i click on it in the file browser it says:

Unable to mount the selected volume.

error: device /dev/hda1 is not removable

error: could not execute pmount

it has previously done this will all of my non-linux partitions, but I figured that was because they were ntfs, I guess I was wrong about that.
Further thoughts?

Rex

add it to your fstab and then mount it

sudo mount /dev/hda1

fstab line:

/dev/hda1       /               ext3    defaults,errors=remount-ro 0    1

---

### Post by rjolley on 2006-09-03
I think I added it to my fstab file which looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1

however when i try the line
sudo mount /dev/hda1

it still says
mount: can't find /def/hda1 in /etc/fstab or /etc/mtab


by the way, thank you very much for the prompt responses.

//side note I have a knoppix cd, and it usually freezes as soon as X loads up.

**edit**
I tried adding that line to my mtab file and got this error:
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

---

### Post by aysiu on 2006-09-03
Paste these commands into the terminal: ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
gksudo nautilus
``` Then press Control-L and type ```
/recovery/home/rjolley/school/cs5340
``` Well, substitute in your real username for *rjolley.*

---

### Post by rjolley on 2006-09-04
Thank you so much, that worked like a charm.
<3 linux community.

---

