---
title: "Making a backup"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-11
Im feeling really pleased with myself, ive just set up my 'office' machine on my network running ubuntu. ( installed an extra 128 megs=now 256) and it runs faster for email and office than my XP machine witth 2X the processor and ram!

Anyway, to the point:

i have my 3 disks:   filesystem, hdd1 and hdd2. 

Hdd1 is a partition drive that contains all my data, but i need to make a mirror of this on hdd2 (a completely sep. hdd). to help protect against hdd failiure. What i want to do is to be able to copy files using the date modified to overwrite the old files. Can this be done by use of the CP command? , as i dont want to wear out my disks unneccasarily by forever copying about a million files every day, that have no reason to be copied:( 

Also, If anyone can point me in the direction of a good on line manual, as I cannot seem to find any "user friendly" linux command references. Unfortunately the built in --help is, as usual, clear as mud :confused:

---

### Post by wishyjr on 2005-10-11
have you tried [www.linuxcommand.org](www.linuxcommand.org) ? i thought that was quite a good one.

---

### Post by davmac on 2005-10-11
I think you need to have a look at the rsync command. I've found it really usefull for mirroring in these sort of circumstances and once you've populated your mirror it then only copies across things that have changed.

There's load more information about how to do this at [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

HTH,

Dave Mac

---

### Post by wylfing on 2005-10-11
Yep, rsync is what you want. If you want to get really clever, make a script that runs the proper rsync command(s) and drop it into one of the /etc/cron.* directories to make it run periodically.

---

