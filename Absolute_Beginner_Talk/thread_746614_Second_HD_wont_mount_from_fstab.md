---
title: "Second HD wont mount from fstab"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Masked Marauder on 2008-04-05
I successfully installed Ubuntu Server 6.06 LTS and set up my mail server, SAMBA and Web Server.

When I saw how little CPU load this put on the machine I then decided to use the server as a local file host too and added a second HD.

The second HD has one partition and was formated with no problems.

So I signed on as SU and changed the SAMBA share on the config file,  and  mounted the HD with the command:

*mount /dev/hda /media/store*

then gave permissions to the mount:

*chmod 777 /media/store*

then restarted the SAMBA.

And all was well, so I added the following line to my fstab:

*/dev/hda1       /media/store    ext3    defaults        0       0*

 I then copied all of my media files and folders over. This was fine and worked perfectly.

Then a few days later I found I had to change the battery in my UPS and had to power down the server. When I started it up again all the data from the second drive was gone. Thinking that it had to be something simple I signed back into my server and checked. The second drive (hda1) was not mounted. I mounted it manually again and restarted the SAMBA, and everything was back.

So I checked and checked and hit a blank.

Why will the drive not mount at start up?

Have I missed something obvious?

fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19457   156288321   83  Linux

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2392    19213708+  83  Linux
/dev/hdb2            2393        2498      851445    5  Extended
/dev/hdb5            2393        2498      851413+  82  Linux swap / Solaris






# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /media/store    ext3    defaults        0       0
/dev/hdb1       /               ext3    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by shawnjones on 2008-04-05
You may want to change your line in fastab to ->

/dev/hda1 /media/store auto defaults 0 0

Thats the only thing that I can think of right now, hope it helps. Another hack could be adding the mount command to your startup scripts.

---

### Post by Masked Marauder on 2008-04-06
/dev/hda1 /media/store auto defaults 0 0

was the correct answer!

Thanks, it is fine now, I thought it would be something simple, oh the joys of being a beginner......

---

