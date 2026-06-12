---
title: "partition error"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-01
might not be the right place, but with all of the dual boots users ubuntu has figured it was worth a shot.. 

when trying to create another partition for ubuntu using partition magic, i keep running into error 1531 code which means to few clusters? i have looked around and haven't really found a solution other than running check disk to check the drive for errors. which i have, and apparently they were fixed, but the error still pops up and in turn the whole process is aborted. any thoughts?

---

### Post by supersonicdarky on 2007-05-01
the ubuntu installer comes with a built in partitioner (gparted). use that instead. it seems partiion magic and linux dont go together very well. (i heard that somewhere)

---

### Post by silent1643 on 2007-05-01
hmm.. okay i will try that and post back, in the past i have had 0 errors with making dual boot partitions using PM

---

### Post by silent1643 on 2007-05-01
when trying to resize the partition with the installer, i recieve an error, and the operation aborts?

---

### Post by Sef on 2007-05-02
> when trying to resize the partition with the installer, i recieve an error, and the operation aborts?

What is the error message?

---

### Post by silent1643 on 2007-05-02
> **Sef said:**
> What is the error message?

Error message with the ubuntu installer is just a general cannot continue or cannot complete operation, aborting.

Error with partition magic is too few clusters.

I have run check disk and i thought the errors were fixed, apparetnly not. Would a fresh format (which i dont want to do but if i have to) fix the problem? Or is there some kind of software i can use to fix my partition?:confused:

---

### Post by silent1643 on 2007-05-02
anybody? im still stumped on this and would love to get ubuntu going

---

### Post by lamalex on 2007-05-02
what kind of computer did this drive come from? I had this same error on an hp drive that had HP's quickplay dvd without booting to windows software on it and it was messing everything up. if you have this get rid of it and try again. Did you use windows chkdsk or fsk? Try using the other one whichever you used

---

### Post by silent1643 on 2007-05-02
hd was purchased new, and installed on a custom built machine.i did chkdsk /f to fix the errors and it found some but im still getting the same errors arge..

---

### Post by lamalex on 2007-05-02
try running fsck on it from the ubuntu livecd

---

### Post by psusi on 2007-05-02
I don't trust partition magic any further than I can throw it.  I've seen it munch too many hard disks.  

If you have windows on there and you just want to shrink it down to make room for ubuntu, just fire up the livecd and use gparted.  When you say you did a chkdsk, you mean you did chkdsk /f in windows, then rebooted and let it do its thing?

---

### Post by silent1643 on 2007-05-02
> **Iamalex said:**
> try running fsck on it from the ubuntu livecd

will do, will post back tonight

---

### Post by silent1643 on 2007-05-02
> **Iamalex said:**
> try running fsck on it from the ubuntu livecd
 how do i do this? just fsck in the terminal is what you mean?

---

### Post by silent1643 on 2007-05-02
okay i got ubuntu to install, but apparetnly i did something wrong during the partition fase of it, now the partition that had my xp install on it is now unallocated lol, any way of getting this back to working order? or at least making the ubuntu partition its max size

---

### Post by superjugy on 2008-01-21
I have the same error 1531 too few clusters. im trying to install ubuntu myself too but i already have 2 partitions. one with my documents and one with my OS win XP. now i want to reduce part of the OS partition and give half to my documents partition and the other half use it to install ubuntu. im trying with partition magic but if you tell me ubuntu can do what i want ill try it with ubuntu. i used partition magic before and it gaved me no problems. i dont know why it is giving my problems now.

---

