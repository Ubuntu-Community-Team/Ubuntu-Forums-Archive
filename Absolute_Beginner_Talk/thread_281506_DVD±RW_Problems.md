---
title: "DVD±RW Problems"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by buckethead27 on 2006-10-21
Hey.

I have a DVD±RW drive, and Ubuntu is reading it as a CD-RW/DVD±R Drive. Two drives at that!

Help.

---

### Post by Klaidas on 2006-10-21
Umm, that probably mean that you cann use that drive to read/burn CDs.
What's the problem?

---

### Post by localuser on 2006-10-21
Have you tried to use the drive to burn CD's and DVD's?  What about reading  CD's and DVD's?  Does it work?

---

### Post by buckethead27 on 2006-10-21
heh. I'm not stupid. It's a dvdrw drive, that is detected as a cdrw/dvd. It reads cd's and dvd's, but does not burn dvds.

---

### Post by localuser on 2006-10-21
> **buckethead27 said:**
> heh. I'm not stupid. It's a dvdrw drive, that is detected as a cdrw/dvd. It reads cd's and dvd's, but does not burn dvds.

Whoa :?

I assure you that my intent was not to infer that you lack intelligence.  As this forum is titled "Absolute Beginner Talk", its difficult to know the level of experience of posters here.

Good luck to you.

---

### Post by konst88 on 2006-10-21
i also have DVDRW drive and it also writes cdrw/dvd.
but i am burning with it both cds and dvds without any problems.

---

### Post by fragos on 2006-10-21
There are mount points in /dev for both CD and DVD but they will both point to the same physical device, perhaps hdc.

---

### Post by buckethead27 on 2006-10-24
Hey sorry for the post above. Didn't mean it like that.

Basically, Ubuntu sees my DVDRW drive as a CD/RW. (That is what it reads when I click on computer.)

---

### Post by localuser on 2006-10-24
[QUOTE=buckethead27;1655873Basically, Ubuntu sees my DVDRW drive as a CD/RW. (That is what it reads when I click on computer.)[/QUOTE]

On my system:

System | Administration | Disks shows "CDROM"
Places | Computer shows "CD-RW/DVD+-R"

Regardless of what it shows, I can burn DVDs on my system.

{edit] Meant to say that even though Disks shows CDROM I can still burn DVD's

---

### Post by buckethead27 on 2006-10-25
Alright. I'll try again. Thanks again for all of your help everyone!

---

