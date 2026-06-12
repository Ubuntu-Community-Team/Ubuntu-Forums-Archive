---
title: "hard drive mounting and usage problems"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2007-08-29
hi-

i formated an old 80 gb digital western hard drive in gparted and now i have one big ext3 partition. i'm using it as a second hard drive to store music, movies, whatever, on. whenever i start the computer the drive isn't automatically mounted. then when i do mount it, whenever i try to move files to it it says 

"Error while copying to '/media/disk'.
You do not have permission to write to this folder."

even when i log in as root it won't give me permission.

while looking all this up in forums and such, most people are talking about the fstab file.
when i look at mine, the 80 gb hard drive isn't listed there, maybe this is the problem?

here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e377f895-5998-4a45-abc8-c8944adfd651 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=90249855-3f15-4042-a8fe-32cc7d8cd3ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


oh well, thanks in advance :)
please helppp

---

### Post by hazelkid on 2007-08-29
yeap, you're right. The partition isn't there. You have to add it manually. Here is a very good reference to fstab-ing :

 [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by onearmedpanda on 2007-08-29
okay i did that
and now it mounts when i start up :)
buttt
i still get the permission error when i try to move files to the drive :(

---

### Post by glotz on 2007-08-29
So what's your fstab like this time?

---

### Post by onearmedpanda on 2007-08-29
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e377f895-5998-4a45-abc8-c8944adfd651 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=90249855-3f15-4042-a8fe-32cc7d8cd3ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1     /media/disk	ext3	defaults	0	0



the bottom one is the one i made

---

### Post by glotz on 2007-08-29
Do a **whoami** to see your username
then do **sudo chown yourusername:yourusername /media/disk**
That will change your current user the owner of the folder.

---

### Post by onearmedpanda on 2007-08-29
it worked :)
thank you soooo much

---

### Post by glotz on 2007-08-29
Glad to be of use! And welcome to the land of the penguin!

---

### Post by bogolisk on 2007-08-29
[quote=Linux Filesystem Hierarchy Standard]
/media : Mount point for removeable media
[/quote]

IMO, /media/X is not the ideal location to mount your disc. It will do no harm now but I wouldn't be surprise of a future version of Ubuntu where /media/ is entirely taking over by hal. You can make up your own path for that, (e.g. /wd80g). The idea is that your own funky naming will unlikely collide with standard name. I have a bunch of such mount-point/disc combos on my box: /wd500, /s80g, /grandpa, etc.

---

