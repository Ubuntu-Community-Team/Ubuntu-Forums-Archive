---
title: "[SOLVED] automount 300gb slave (sdb1)"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by mandrill on 2007-09-26
Greetings!

Didn't see anything already posted that answered all of my questions, so, here goes....

First, my fdisk results:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36106   290021413+  83  Linux
/dev/sdb2           36107       36483     3028252+   5  Extended
/dev/sdb5           36107       36483     3028221   82  Linux swap / Solaris

My question in a nutshell: 

       How do I turn the 300gb sdb1 into a usable, auto-mounted media/file storage device? ubuntu sees it, apparently it is booting, but I have no clue what to do next. This is a pc with ubuntu as the only operating system, but files will be shared via LAN with 'doze. (ntfs)

I can follow directions pretty well, so if one (or more) of you nice folks can take pity on me it would be well-appreciated! Hope to be on the advice-giving side of things eventually!

---

### Post by Pumalite on 2007-09-26
You have a Linux OS installed in sdb. You want to reformat it? What?

---

### Post by mandrill on 2007-09-26
Yes, forgot to mention - I originally tried to install on the 300gb drive, but mobo unable to handle, so I switched them - now I am, in fact, looking to correctly format/partition/mount the 300gb drive - without an OS - again, any help you can provide is greatly appreciated!

---

### Post by Pumalite on 2007-09-26
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
And make a large partition of your hard drive and format Fat32 if you want to share data with Windows, or ext3 is you want to use only with Ubuntu.
(Make sure you point to sdb)(right hand corner)

---

### Post by mandrill on 2007-09-26
Thank you, I was pretty sure that was the first step. How large a partition can fat32 handle? Or, more directly, how large should I make the partition? On windows (ntsf) you only have to leave around 8mb....


OK...ran sudo apt-get install gparted and sdb1 is now formatted as fat32, size = 276.59gb, used = 138.27mb. and unused = 276.45gb.....sdb 2 shows as "extended" @ 2.89 gb and sdb 5 shows as "linux-swap"  @ 2.89 gb.....still not sure what to do next....as always, help is appreciated!

---

### Post by mesilliac on 2007-09-26
You can install gparted via Add/Remove in the main ubuntu menu.

Just fill the whole disk up :). FAT32 can support up to 2TB, but does have other limitations (such as a max file size of 4GB I think). GParted will set some of the space aside for the filesystem automatically.

Oh and be careful!

---

### Post by mandrill on 2007-09-26
I swear, people, one day I'll be helping, too! Please see edited post above....now what? - 

Rebooted, there is "disk"....COOL! - Thank you, folks! Been scratching my head over this for awhile....

But, how do I make auto-mount, and access as user? I think I'm wanting to do this, that i copied from a similar thread...."installed a slave drive I will use for storage and it is named disc. How do I change the name and also not have to log in to it when I first open it? I am using 7.04." or - possibly mount it in home folder? Right now, my 300gb slave is called "disk" and I have to log into it) - the answer was for ntfs, though...

---

### Post by mesilliac on 2007-09-27
For this you need to edit the file "/etc/fstab", which specifies which drives are mounted at startup, and how.

There are some good instructions here:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Follow the instructions for setting it up manually and you will learn more about how it works :). To find out what your user id (uid) is, type "id" in a terminal. To edit fstab, type "sudo gedit /etc/fstab".

---

### Post by mandrill on 2007-09-27
Thank you, mesilliac & Pumalite! This is good stuff - have learned more in the past couple days than I thought possible. Definitely not in Kansas anymore!  :)

---

