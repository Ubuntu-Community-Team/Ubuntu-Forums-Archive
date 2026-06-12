---
title: "problem mounting cd"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Caitilin on 2007-05-30
hi, 

I'm trying to reload my data on Feisty Fawn. 

I have most of my cd's, so the cd player works. These cd's all had directories of data. 

Now, the next three cd's have files, if memory serves, or a file/dirctory mix. 

All three give hte error: 'unable to mount the volume 'volumename' 

and under details,

details: mount: block device /dev/scd0 is write-protected, mounting read-only mount: not a directory

and an ok button. 
I made all these cds with xp by dragging and dropping..nothing different. One of htese has my uni files on them and I need htem. Help!

---

### Post by kernel tom on 2007-05-30
a couple things could be the problem here.

Depending on the program you used, and assuming you actually burned and finalized the CD, you may have formatted this data cd in an incompatible format.  Especially seeing how it was a windows cd.

to get it to mount as read only, which should happen nomatter what do the following

sudo mount -t iso9660 -o ro /dev/cdrom /cdrom

should be able to pull whatever u need off of it

---

### Post by Caitilin on 2007-05-30
At the risk of being very new and a bit of an idiot...

Where do I type this in?

---

### Post by Caitilin on 2007-05-30
At the risk of being very new and a bit of an idiot....

Where do I type this in?

---

