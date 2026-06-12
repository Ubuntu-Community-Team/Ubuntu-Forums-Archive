---
title: "Cdrom wont automount &amp; a quick lirc question?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by asmugone on 2007-04-10
Hi gang, Just switched over from windows and I have got say that I love the new face of linux.! Anyway now that I am no longer a guru of my os, I find myself once more in newbie forums. Heres my problem.

I rearanged my hdd and dvd-r, its a media center and I cant resist messing with it! :)
Now for some reason I cant get my dvd rom to auto mount to the desktop! If I go to the cdrom file in the base filesystem directory then I can see whats on the disc and im tinkering trying to fix this. 

Heres what i tihink happened. Before the great tinkering my dvd has set as /media/hdb
Now its hda. So i went into /etc/fstab and edited the file to change it from hdb to hda.
Thats how I can now look at the files and use the disc, but still will not automount or show me an icon on the desktop! Someone please help this poor noob!

Oh second question, I have gotten lirc up and running, and am using the lirc mouse demon, with a hauppgauge 350 remote and homebrew serial ir recieve *I built it, works great! detailed howto for the other noobs coming soon!*

My problem is this, in lircmd.conf I have options for like northeast etc. but instead of slaving to a sing button i want it to go that direction when I press right arrow and up arrow in order to go to the north east. I have been digging around with google but havent found myself any love yet.

Is this even possible with lirc? Example would be very welcome. Thanks Gang!!

---

### Post by devnulljp on 2007-04-10
post your fstab...

---

### Post by asmugone on 2007-04-10
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=36aae607-a7a2-406d-9bc4-c2bddd0d7781 /               ext3 defaults,errors=remount-ro,noatime,data=writeback 0 1
# /dev/hdc5
UUID=8e0dba8f-2313-4e03-91bb-5febcd5c167c none            swap    sw              0       0
/dev/hda        /media/dvdrecorder   udf,iso9660 user,noauto     0       0

---

### Post by asmugone on 2007-04-10
Hrm, is there some way to relink the files besides fstab, maybe that is where my problem lies??? Come on guys!!! a command line program anything???

---

### Post by asmugone on 2007-04-10
Hey gang! Got it!, Had to go through and change the fstab for hda so instead of dvdrecorder which device manager said it should go to, instead I made it cdrom0 , before I had just put cdrom and that is no doubt why I had so many problems. Now its on to seeing about the lirc question!

---

