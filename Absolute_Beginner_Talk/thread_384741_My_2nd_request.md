---
title: "My 2nd request"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Jerry Wolczanski on 2007-03-14
I've got some backup software called "cpbk" on my machine.  This software appeals to me as it will do a mirror backup (I have an external HD).  Darned if I can get this software to run.  I've installed software before but this one eludes me.  There appears to be a script - maybe I just need to run that from the terminal - but I don't know how.  Anybody help with that?

Sbackup is also loaded (Ubuntu 6.10) but it's not clear to me how I make a mirror.  Additionally, I can't use the default backup directory (/var/backups) as it won't let me mount my usbdisk there (not a block device)

The option exists for a custom local backup directory.  I can't seem to get that to point to my usbdisk.

I can also run the external drive off a sata connection (e-sata) if that helps.

but again - I've got a G4 Mac and have a clone backup.  I like the concept of being able to mirror my drive.  Lord knows I've got enough room (250GB)!

any help would be appreciated.
Thanks
Jerry

---

### Post by mikesignguy on 2007-03-14
telling people what  you want to do and  they    may steer you in  different direction


try searching  for stuff on "rysnc" it updates files without copying all the data ... only the changes   ... i think that's what you want

i think this is what you  are  looking for

---

### Post by aysiu on 2007-03-14
*rsync* is great. Read more about *rsync* and some other backup options here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by Jerry Wolczanski on 2007-03-15
Thanks to both of you!

I think cpbk, SBACKUP, and a few others might just be GUI's and front-ends for RSYNC.  I've received some advice on how to run cpbk from another source....but will keep RSYNC in my back pocket.  It seems all roads lead to RSYNC.
Thanks again
Jerry

---

