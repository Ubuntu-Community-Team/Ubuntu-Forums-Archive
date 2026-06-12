---
title: "Typo in my fstab-can't access /dev/hdax now!"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-01-30
Added an equal sign instead of a space in an entry to my Ubuntu drive, hda7.  (I was modifying for writeback)

Of course every attempt to access it (even from windows with LTOOLS) fails because it's not mounted.

Of course recovery console fails because there is no hda7 mounted!

Only thing I can think of is if I can mount it from the UBUNTU CD's terminal and nano the offending equal sign out of the fstab file??

(I HOPE!)

Help....  :)

---

### Post by jpeddicord on 2007-01-30
Yep, your best bet is to mount it from the Live CD. Just run ```
sudo mount /dev/hda7 /media/hda7
``` and it should mount to the CD from where you should be able to edit it.

Jacob

---

### Post by emarkay on 2007-01-30
Crossing my fingers while I reboot...  Be back in a bit...  :)

---

### Post by emarkay on 2007-01-30
I get: 

mount: mount point /media/hda7 does not exist

Any other ideas?

---

### Post by emarkay on 2007-01-30
I have edited the file by making a /tempmount, but now how do I get the /tempmount dir to  hda7?

---

### Post by dwblas on 2007-01-30
You have to mount /dev/hda7.  If you have mounted /dev/hda7 at /tempmount then you have edited the file that is on /dev/hda7=/tempmount.  If not, you have edited some other file that is on whatever drive is mounted on /tempmount or it's parent directory(s). (assuming you did save the file after editing).

---

### Post by emarkay on 2007-01-31
I gave up and reloaded Ubuntu...

I will present a gift to noobs later on - a step by step typical installation of Ubuntu - from start to finish  (In case I need to do it again, and, why not, I'll share it.)  

Thanks.

***PS: BTW, triple check edits to to your fstab - especially on your "/" volume!! ***  ;)

---

