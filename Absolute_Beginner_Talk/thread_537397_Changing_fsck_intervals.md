---
title: "Changing fsck intervals?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by TomR55 on 2007-08-28
I understand that tune2fs is provided to allow us to change the intervals (either by time or by number of boots) that fsck is run at boot time. The manpage for this command suggest that something like:

sudo tune2fs -c 100 /dev/sda1

should result in fsck being run every 100'th boot. But, I get a complaint about

tune2fs 1.40-WIP (14-Nov-2006)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

Now, I am no expert at this, so I include my fstab below:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=12e35999-a970-47b4-ac7a-38e9776d5097 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5747599e-930a-4d3b-a852-5786d74271f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=a7a3890f-8b07-46f8-b6ae-592d8320359d  /boot ext3 defaults 0 0


Could someone tell me what I'm doing wrong here? I really would like to fsck every 100 or so cycles.

Thanks in advance.

PS:> Running Ubuntu Feisty ...

TomR

---

### Post by ramjet_1953 on 2007-08-28
A much easier and safer way to control fsck scanning is with [COLOR="Blue"]Bonager[/COLOR].

It's available in the repositories.

[COLOR="Red"]sudo apt-get install bonager[/COLOR]

Here's a link for further info: [http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

Regards,
Roger :cool:

---

