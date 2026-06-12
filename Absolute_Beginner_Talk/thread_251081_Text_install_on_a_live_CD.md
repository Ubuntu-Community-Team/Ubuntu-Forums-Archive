---
title: "Text install on a live CD"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by phantomreaper on 2006-09-04
Is it possible to get a text install started instead of having to go into Ubuntu and then installing it...I have a crap-slow CD-ROM drive...am getting better one soon but want to try Ubuntu now.

---

### Post by GuitarHero on 2006-09-04
Not with the live cd, you need the alternate install cd.

---

### Post by Paul133 on 2006-09-04
I'd reccomend the alternate or server install. With the alternate CD, you can install Ubuntu with a text install or do a server install. If you do a server install (my computer was only able to do a server install; it kept hanging during a desktop install, even a text one), then you'll come to the command line, and once you're logged in, just type ```
 sudo apt-get install ubuntu-desktop 
``` Good luck!

---

### Post by phantomreaper on 2006-09-04
Thanks. I have a text install CD of Ubuntu Breezy Badger then I'll upgrade it...can I get packages from all the Ubuntu CDs ie. Ubuntu, Kubuntu, Edubuntu?

---

### Post by ds[de] on 2006-09-05
> **phantomreaper said:**
> Thanks. I have a text install CD of Ubuntu Breezy Badger then I'll upgrade it...can I get packages from all the Ubuntu CDs ie. Ubuntu, Kubuntu, Edubuntu?

Sure you can.
As long as you know the name of the packages, you can all install them via
$ sudo apt-get install <package name>

If you'd like to use a different desktop environment, you can also do that by typing 

$ sudo apt-get install kubuntu-desktop / xubuntu-desktop / etc.

Regards,
ds[de]

---

