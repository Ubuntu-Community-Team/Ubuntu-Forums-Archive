---
title: "I/O error copying from CD to desktop"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by savethewabbit on 2008-02-06
hi, 
i have a problem while trying to copy a file from a CD to my computer.
specifically, i'm trying to copy World of Warcraft's installer tomes (about 630 mb each). 
i select the file on the cd and copy it, then i tried about every folder on my computer and try to paste it.
it seems to work, but when it's almost done it says:
"Error "I/O error" while copying "/media/cd...ome 4.mpq"."

and that's it :\ 
i tried changing cd drive and nothing changes. i am also sure that the cds work because i installed WoW with them back when i had windows. i also used them only once so i don't think they're ruined or anything. 

also, i'm stuck at the 4th cd. the first two files from the first two cds were copied without problems. the third cd gave me this same error a couple of times but eventually worked. this one i've been trying since yesterday to no avail.

help anyone?

---

### Post by az on 2008-02-06
Try using data recovery software to image the disk.

Install gddrescue and run

sudo ddrescue /dev/cdrom image.iso log

And let it run.

---

### Post by savethewabbit on 2008-02-06
thanks for replying :) 
however it's been showing this (no changes at all) for a couple of hours:

```

Initial status (read from logfile)
rescued:         0 B,  errsize:    2048 B,  errors:       4
Current status
rescued:   657057 kB,  errsize:   6432 kB,  current rate:        0 B/s
   ipos:   656896 kB,   errors:    1792,    average rate:    60219 B/s
   opos:   656896 kB
Splitting error areas...

```

since it says there are errors, i'm not sure it's supposed to happen...

---

### Post by yaknowwat on 2008-02-06
I/O error is exactly what it sounds like...

Data In / Out Error

Something on your CD is bad.
Normally a scratch in a place where data resides or something bad.

Scratches don't have to be big they just have to hit a certain point like the disk label or the sector where the data is, a scratch on top side of the disk can be just about as bad as the bottom too.

Have you tried cleaning your CD with something recently?
Certain things can erode a CD.

---

### Post by savethewabbit on 2008-02-06
i never cleaned the CD because it's not more than a month old...
do you think it's possible to solve the problem? like, cleaning the CD? i would try but i wouldn't want to mess things up more than they already are.

also, would a scratch on the CD be the only cause for this error? as i said i only took out the CD from its case once, and it was when i installed the game (and it installed just fine, no errors). it couldn't be something wrong with my pc, could it?

---

### Post by az on 2008-02-09
If this happens with every cd you try to copy, then it's ahardware issue.  If it only happens with this one, then that's conclusive proof that the problem is with that one disk.

Save the image.iso and the log file to an external drive.  Find an old computer with two optical drives.  Boot the Ubuntu live cd and plug in your external drive.  Try to image the cd again on that computer.

sudo ddrescue /dev/cdrom1 image.iso log -C
(Note the -C flag which makes it Complete the image, writing only the bad spots - it uses the log to tell where the bad spots are.  Note also that it's /dev/cdrom1 and not /dev/cdrom.  This is becuase you are running from the live cd.)  

If it still can't read pas the errors, try disabling your cdrom's DMA.  You can also try putting it in PIO mode, if your copmuter is old enough.   You change these settings in the bios.

Older cdroms can often read corrupted disks like that better than modern cdroms.

---

