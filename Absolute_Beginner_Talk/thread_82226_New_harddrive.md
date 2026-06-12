---
title: "New harddrive"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by bete on 2005-10-26
I installed a new harddrive, but i dont know how to get it to work on linux.
I was hoping it would auto detect and just be there when i booted.

---

### Post by TimonVO on 2005-10-26
Is your harddisk already partitioned?

---

### Post by bete on 2005-10-26
I dont know.. I dont care what is  on it tho.

---

### Post by TimonVO on 2005-10-26
You just bought in the shop? I mean, it doesn't come from another pc?

---

### Post by bete on 2005-10-26
[QUOTE=TimonVO]You just bought in the shop? I mean, it doesn't come from another pc?[/QUOTE]

Well i guess there is something on it, maybe an OS. 
I would guess i had to format it. But dont know how ^^

---

### Post by wishyjr on 2005-10-26
if you dont care about whats on it then the ubuntu installer can format and partition it for you. :)

---

### Post by bete on 2005-10-26
[QUOTE=wishyjr]if you dont care about whats on it then the ubuntu installer can format and partition it for you. :)[/QUOTE]

You mean i put in my ubuntu cd and reboot and do something from there?

---

### Post by wishyjr on 2005-10-26
hangon! did you say you have ubuntu already installed? and the harddrive you are refering to you want to work in ubuntu? i think then you need to mount the new drive to view it on your desktop or whatever, so i wouldnt think you needed the install cd for that.

do you know if the drive is an IDE drive? or a SCSI/SATA?

---

### Post by bete on 2005-10-26
Yes i already have ubuntu installed, i put in a new harddrive in my computer today, so i was just wondering how i can get it to "work".

Mount sounds like an idea...

---

### Post by wishyjr on 2005-10-26
well.. im not sure if im correct here but try:

**fdisk -l ** in a terminal and see what it shows you.

how many hard drives do you have in your pc? 2 (with the new one?) If so then at a guess i'd try:

**mount /dev/hdb** maybe with a **sudo** in front. But im not sure. :)

EDIT!! actually i think it'd be **hdb1**, sorry. i'm only a learner myself.

also, if that works and you mount it, you'll find that when you reboot it'll vanish again and you'll have to remount it! to sort this i found this thread:

[http://www.ubuntuforums.org/showthread.php?t=78137&highlight=mounting+hard+drive](http://www.ubuntuforums.org/showthread.php?t=78137&highlight=mounting+hard+drive)

good luck!

---

### Post by bete on 2005-10-26
> bt@ubuntu:~$ sudo mount /dev/hdb2
mount: can't find /dev/hdb2 in /etc/fstab or /etc/mtab
bt@ubuntu:~$ sudo mount /dev/hdb1
mount: /dev/hdb1 already mounted or /boot busy
mount: according to mtab, /dev/hdb1 is already mounted on /boot


When i look in system >> administration >> disk
I find it, it has two partitions on it, i can format one of them, but it is only on 300 megabytes or so, the other partition is 10 gig but i cant format it or enable it.

---

### Post by wishyjr on 2005-10-26
ok, so it *did* auto detect it then yes? if its hdb1. and you can see whats on it? Places>> Computer>> Filesystem? hmmm if its not letting you format it etc. then its maybe a permission issue which  i dont really know much about.. sorry mate. 

make sure that its the right drive your trying to enable/format though -you dont want to erase ubuntu!! :)


EDIT: ok, had a qick skeet about and found this:
[http://www.ubuntuforums.org/showthread.php?t=79050&highlight=format+hard+drive](http://www.ubuntuforums.org/showthread.php?t=79050&highlight=format+hard+drive)

it seems a little more educated than my replies so i'd reboot and try the commands in this thread. good luck!

---

### Post by SilentCacophony on 2005-10-26
Hi. I can probably help you mount your new drive in Ubuntu, but first I'd need to know what you wish to use it for.

Do you wish to use it for extra file storage, such as for downloaded files?

If so, then you'll need to know what is already there to work with, and whether you want it to be accessible from ubuntu only or also from Windows. As previosly mentioned, an easy way to see what's there is to run:

**sudo fdisk -l**

in a terminal. If you can post the result back here, that would help.

---

### Post by bete on 2005-10-27
[QUOTE=SilentCacophony]Hi. I can probably help you mount your new drive in Ubuntu, but first I'd need to know what you wish to use it for.

Do you wish to use it for extra file storage, such as for downloaded files?

If so, then you'll need to know what is already there to work with, and whether you want it to be accessible from ubuntu only or also from Windows. As previosly mentioned, an easy way to see what's there is to run:

**sudo fdisk -l**

in a terminal. If you can post the result back here, that would help.[/QUOTE]

> 
Disk /dev/hda: 4325 MB, 4325529600 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         500     4016218+  83  Linux
/dev/hda2             501         525      200812+   5  Extended
/dev/hda5             501         525      200781   82  Linux swap / Solaris

Disk /dev/hdb: 10.8 GB, 10800857088 bytes
255 heads, 63 sectors/track, 1313 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        1313    10442250   8e  Linux LVM


I want to use it for storage of downloaded files.

---

### Post by SilentCacophony on 2005-10-27
Hi. Looks like this is your newly installed drive?

```
Disk /dev/hdb: 10.8 GB, 10800857088 bytes
255 heads, 63 sectors/track, 1313 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 13 104391 83 Linux
/dev/hdb2 14 1313 10442250 8e Linux LVM
```

If so, I would recommend that you download and install gparted using Synaptic, or from a terminal:

```
sudo apt-get install gparted
```

Open Applications -> System Tools -> Gparted, and assuming that you know that it's the second drive that you have newly installed that I listed above, select /dev/hdb from the dropdown button on the upper right.

You should see 2 partitions. If you just want one big partition filling the whole drive, then select the partitions and delete each one. Then, select 'New', and make one partition as large as the drive. If you don't, and won't, use Windows, then ext3 is a good choice of filesystem to use for that partition, otherwise FAT32 (vfat) is a good choice for sharing data between Windows and Linux.

Then go to System -> Administration -> Disks. Select the second harddrive from the list on the left, then select the 'Partitions' tab. It should show /dev/hdb1 as the 'Device', and whatever you chose for the Filesystem. You should select the 'Format' button to format the partition now.

The 'Access Path' may be blank. If it is, select 'Change', navigate to *Filesystem* and enter the */media* folder. Select 'Create folder' and choose a name for the mount point. Make the folder's name whatever you want the disk to be named. Finally, on the 'Status' line, select the "Enable" button, which will mount the partition. Select 'Ok' at the bottom, and you're done.

If you chose ext3 for the filesystem, you should have full permissions for the drive. As for FAT32 (vfat), I'm not sure it will do that, so you can post back if you have permissions problems.

---

