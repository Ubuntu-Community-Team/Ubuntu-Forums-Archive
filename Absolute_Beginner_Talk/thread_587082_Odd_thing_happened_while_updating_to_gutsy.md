---
title: "Odd thing happened while updating to gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by LowSky on 2007-10-22
I was updating my laptop from Fiesty to Gutsy and all the files downloaded fine, but something odd happen toward the end of the installation and the computer locked up, and I had to reboot it, when I did The new version of Ubuntu seemed to be installed just fine except for some error for installing pakages.
 It asked me to type (and if I type the code wrong, sorry I'm doing this from memory)
using sudo-i```
 dpkg --configure -a
```

after that everything was fine, and I could install new programs and drivers with no other issues.

Just wanted to know if anyone else was having this command come up, or anyone know the issue?

BTW the laptop is an old Dell Inspiron 8100, P3 1ghz, 256 RAM, Nvidia geforce 2, 30GB hard drive.

---

### Post by evilregis on 2007-10-22
At what point did it lock up?  Were you connected to the net during the install?

I thought my install was hanging... turns out it was just busy repos.  During the install you can get around this by unplugging your network cable and just strictly installing from the CD itself, then picking a new mirror after the install is complete and updating from there.

---

### Post by LowSky on 2007-10-22
No it did lock up, but it must have finidshed the instalation and was trying to build the the repositoires but I turned off my wireless card, and it gave no warnings or even flinched. 

Yeah I know the laptop is old and slow but the busy light was just on and not blinking and there was no hard drive spin occuring.

I dont care if the laptop works well because it a back up machine to my desktop which has had gutsy since tribe 4. Maybe Ill wipe the thing cean and do a fresh install of xubuntu

---

