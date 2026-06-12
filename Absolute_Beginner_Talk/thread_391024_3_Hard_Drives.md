---
title: "3 Hard Drives?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by acorn22 on 2007-03-22
Is it a bad Idea to have 3 hard drives? Like this.

IDE: 
HD one, HD two

IDE:
DVD-RW, HD three

Is it even possible?

---

### Post by mrmonday on 2007-03-22
You shouldn't have any problems, except number 3 will go considerably slower than 1 and 2. Just wondering... Why did you ask? are you planning something?

---

### Post by thingy on 2007-03-22
The only downside is:

If IDE 0 has one slow hdd and one fast hdd then you will not get max performance out of the fast hdd.

And as IDE 1 had one DVD-RW and one HDD, the HDD is going to give crappy performance because it has to share the interface with the DVD-RW.

I wouldn't worry about this...honestly...you won't notice anything in your day to day usage.


[COLOR=#800080]Q. What do you      call an ant who skips school?
A. A tru*ant*.

[/COLOR]

---

### Post by Muzik83 on 2007-03-22
(This is more of a basic hardware question, but I can put an ubuntu spin on it by the end of the reply)

Yep this is entirely possible.  You will need to set one drive to be a master and one drive to be a slave.

IDE1:
  Master: Hard drive (this will be /dev/hda in Ubuntu), this is what you will boot off of
  Slave: Hard drive (this will be /dev/hdb in Ubuntu)

IDE2: 
  Master: Hard drive (this will be /dev/hdc in Ubuntu)
  Slave: CDROM (this will be /dev/cdrom in Ubuntu)

The "Master/Slave" setting is done through jumpers.  Consult the documentation with the drives for how to set if it is a master or not.  You may also be able to use cable select if your hardware supports it (but again, consult the documentation that came with your hard drives and cdrom).

I hope you find this useful

-sean

---

### Post by acorn22 on 2007-03-22
Thanks everybody.

I'm not worried about performance as the rest of my system is pretty weak. (Celeron 1GHz, 256MB) and each hard drive is only 15 gigs.

Muzik83 made me think of something. Should the DVD drive be master or slave, or does it even matter?

Again thanks for all the replies :)

---

### Post by mrmonday on 2007-03-22
It doesn't really matter, but it is best to have it as slave... I can't remember why, its ages since I last looked at this kind of thing.

---

