---
title: "DVD Shrink only recognizing one drive"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-09-02
Right so, I have a CD-RW drive set as master  (shows up as :/I) and a DVD-RW as slave, which shows up as G:

When I autodetect, they both come up as the same thing though: /media/cdrom0  

When I browse the directory to input a different path for G: however, there is /media/cdrom  too, but setting it to that, makes no difference, as dvd shrink still only gives me I: as a drive option. 

I remember that when I was using Zenwalk, I had to set my CD RW as /dev/hdc in order to get it to be detected, but in this case it's obviously different. What to do, what to do ? 

Doug

P.S. Windows version is set to Win 2000

---

### Post by orb9220 on 2006-09-02
Yeah I had problems with dvdshrink with two drives too. Never did solve it.
Also FYI don't rip a dvd down to an iso then think to recompress again  shrink gets funny and the compression slider goes all funky,

Example: Ripp Movie that spans two discs and you want to put both onto one disc. Do not use iso's but file folders to rip to then you can import both and make it into one disc.

---

### Post by Sweet Spot on 2006-09-03
Ok. Not very encouraging, but thanks ? :p   Has *anyone* had the same problem and actually solved it ? At this point, I may very well just switch the IDE cable around if I can't resolve it any other way. 

Doug

---

### Post by Sweet Spot on 2006-09-03
A-HA ! I think I've got it, by George ! It appears that once a DVD is inserted in the drive, a new directory is created, which obviously is neither Cdrom or Cdrom0. It actually just says dvdrecorder upon insertion. So, I directed winecfg Drives tab to that directory, and viola ! It's now analyzing the movie ! :mrgreen:

Hopefully the rest will work just as well. 

Doug

---

### Post by orb9220 on 2006-09-03
Yea! glad it worked for you.

---

