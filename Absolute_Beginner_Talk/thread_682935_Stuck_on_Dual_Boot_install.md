---
title: "Stuck on Dual Boot install"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Dunover on 2008-01-30
Hi
I have a large disk that has been partioned already...at the install process, I am totally confused

here is where I am at

Prepare Partitions

/dev/hda
  /dev/hda1 ntfs  /media/hda1   25111 MB  uknown
  /dev/hda5 ntfs  /media/hda5   36380 MB  uknown

I want to install a dual boot  windows2k is already here  "/media/hda1" 
(don't want to mess that up!)  

and I want to install ubuntu here  /media/hda5

BUT don't know what to do next...**exact** instructions would be great as am new!

Corisa

---

### Post by jan quark on 2008-01-30
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
this is a step by step instruction by aysiu with pictures :)
read it slowly nobody is chasing you

and if question crop up ask us :)

---

### Post by Dunover on 2008-01-30
Yes, I have already read that til blue in the face... LOL

BUT in my situation....am not wanting to kill my win install

I have tried the other option and it "appeared" to want to resize the partition on hda5, which the whole partition I was hoping to use.... so I resized the little bar, to almost the whole thing... and this where am at...  does this look like it is going to leave  hda1 alone, and install ubuntu on hda5. I did have a temp in stall on another disk, that it appears to want to Transfer over that is the slave?

 
 Migration Assistant:
 Ubuntu 7.10 (7.10) (/dev/hdb1):
 cori: Mozilla Firefox, Evolution


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 IDE1 master (hda)
 IDE1 slave (hdb)

The following partitions are going to be formatted:
 partition #6 of IDE1 master (hda) as swap
 partition #3 of IDE1 master (hda) as ext3

---

### Post by Seisen on 2008-01-30
The easiest way to do this is to use gparted and completely erase hda5 if you want to completely use that whole partition for Ubuntu. This will leave you with free space then when it ask you where you want to install Ubuntu select the option that says " Largest continous free space" or something like that.

---

### Post by bodhi.zazen on 2008-01-30
Hard to follow exactly ...

From what you are saying you want to install here :

> /dev/hda5 ntfs /media/hda5 36380 MB uknown

OK, so, first, partitions are /dev/hda and NOT /media/hda (/media/hda is the so called mount point, /dev/hda is the physical partition).

Second, you want to unmount the partition before you install.

Third, that partition is NTFS. To install Ubuntu you will need 2 additional partitions, one for Ubuntu (ie root or /) and one for swap. You will need to format both spaces as you can not install onto a NTFS partition.

See these links :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

So, with me so far ?

Then at the partitioning part of the install, you set one partition as / , format it to ext3
set a second partition as swap, format it
mount your windows partition (if you like), I suggest a manual mount point like /media/windows, DO NOT FORMAT this partition.

MAKE SURE YOU UNDERSTAND LINUX TERMINOLOGY or you will format the wrong partition.

---

