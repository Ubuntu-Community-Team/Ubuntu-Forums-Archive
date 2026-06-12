---
title: "can't play music cd's"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-20
Hi when i put a cd into the drive there is a little bit of noise but no program opens. it says that sound juicer is supposed to open in the preferences but it doesn't. i manually opened sound juicer but it doesn't see the cd. also i tried another way. i put an mp3 file on the desktop and it didn't want to play that either. i opened several data disks and the system sees them ok but just won't play music. i have only had ubuntu on this laptop a couple of weeks so i am not sure what to do. i have gotten all the upgrades.

---

### Post by mikewhatever on 2007-02-20
Not quite sure, but I wonder if the restricted formats have something to do with it.
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

Edit: strange, it works for me
"https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29"

---

### Post by rapattack1 on 2007-02-20
that link doesn't seem to be working. what is a restricted format? i mean what format is restricted? i is just an ordinary music cd, factory made.

---

### Post by Maestro23 on 2007-02-20
> **rapattack1 said:**
> that link doesn't seem to be working. what is a restricted format? i mean what format is restricted? i is just an ordinary music cd, factory made.

Restricted Formats (mp3, playing DVD): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If you want to play mp3 files, you will have to install the correct plugins for your player and Ubunutu version.  Find your verison and follow the directions.

---

### Post by rapattack1 on 2007-02-20
that url doesn't work either. um i am mostly trying to play ordinary factory made cd's but yeah it would be nice to have an mp3 plugin. this is just a cd drive so no dvd's will be played.

---

### Post by Maestro23 on 2007-02-20
> **rapattack1 said:**
> that url doesn't work either. um i am mostly trying to play ordinary factory made cd's but yeah it would be nice to have an mp3 plugin. this is just a cd drive so no dvd's will be played.

Strange, both links provided work for me.  When you put a cd in the drive, does it auto mount and put an icon on your desktop?  Does the program you are trying to play the cd thru, see the cdrom device(pointed at the right drive in its preferences)?

Open a terminal and type:

> cat /etc/fstab

Find the entries for your cd drive.  Will probably be something like:

/dev/hdc... This is what your music player should be pointed to in its prefs so it can find the cd.

---

### Post by rapattack1 on 2007-02-20
no it doesn't mount or show an icon on the desktop. maybe there is something happening with my isp with some sites.....i dunno it is acting a bit strange tonight.
both sound juicer and rhythmbox don't reacte or show an error whatever.

here is what the terminal came up with:
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0b39e49c-f6d4-4c23-bf0f-52180fb7498c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a12e54af-3e98-4310-8403-94514054f441 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Maestro23 on 2007-02-20
> **rapattack1 said:**
> no it doesn't mount or show an icon on the desktop. maybe there is something happening with my isp with some sites.....i dunno it is acting a bit strange tonight.
both sound juicer and rhythmbox don't reacte or show an error whatever.

here is what the terminal came up with:
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0b39e49c-f6d4-4c23-bf0f-52180fb7498c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a12e54af-3e98-4310-8403-94514054f441 none            swap    sw              0       0
[COLOR="Red"]/dev/hdc[/COLOR]        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

In red is your cdrom.  Whatever player you are using, make sure it is set to look for a cd in this device.  I had to go into vlc(videolan) player and point it to my correct DVD drive.

Should be able to change this in the preferences of the program you are using to play your audio CDs.

---

### Post by rapattack1 on 2007-02-20
well soundjuicer cd ripper mentions my cd drive in the preferences.

---

### Post by 512mattw on 2008-03-25
when I put a cd into my gateway gt5654 cd/dvd drive (just one drive dvdrw) an icon appears on the desktop "CD-ROM disc" however it wont play with any software-sound juicer, banshee...
DVDs play fine with menu and all-sound works great.  Banshee recognizes theres a cd in the drive but doesn't identify tracks of artists.  Right clicking on the desktop cd icon and going to settings under volume gives me no entries/all blank for mount ponit, file system, and mount options.  In the same window it says the cd is not mounted but shows how much data is on disc.  I suspect this may have something to do with it.  By running the "cat /etc/fstab" in terminal I get....
danielleandandy@danielleandandy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cbd31ac4-b650-4654-9aa5-30346413352f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ba521b2d-a6cf-4ce2-8bbe-e5914f85410b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

can someone please help.  I just want to listen to a regular store bought music cd on my computer.

new to Ubuntu-
Matt

---

