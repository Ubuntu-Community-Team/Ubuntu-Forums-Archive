---
title: "how do you run mac apps on ubuntu?"
date: 2008-05-29
forum: Apple Hardware Users
---

### Post by rossmc92 on 2008-05-29
I was just wondering how to run osx files e.g. dmg on Ubuntu. It should be possible because my Ubuntu is on powerpc g4 mac.

---

### Post by croto on 2008-05-29
As far as I know, it is not possible, even running on the same hardware platform (PPC). The main problem is that the program would try to use operating system subroutines belonging to macosx, which don't exist in ubuntu. For windows apps, people have written a replacement for those libraries and subroutines (WINE project), but there's nothing of the sort for mac apps.

---

### Post by mfox on 2008-05-29
Actually, there is a program called Mac-on-Linux that should be on your Ubuntu depository and will do what you're looking for.  At least it does on versions below the present one (8.04).

---

### Post by BladeMelbourne on 2008-05-29
I second the MoL suggestion. I'm running 8.04 with my Gutsy kernel (2.6.22), which allowed me to compile/run MoL without problems. I could not compile MoL against 2.6.24.

Performance isn't great - e.g. CPU is fully utilised when playing YouTube inside it (G4 1.42 GHz + 1GB RAM).

[http://mac-on-linux.sourceforge.net/news.php](http://mac-on-linux.sourceforge.net/news.php)

---

### Post by mfox on 2008-05-29
BladeMelbourne, could you explain how you did this or refer me to a site with directions.  I'm pretty new on Linux, and I did try to compile MOL to run on Hardy from directions on another site, but not against an older kernel and what I tried didn't succeed.

---

### Post by rossmc92 on 2008-06-15
Unfortunately you need an existing installation of osx for mol and I only have a Leopard disc which has no chance of being able to run successfully on my mac. I am looking for something along the lines of Wine but a ppc version.

---

### Post by cyberdork33 on 2008-06-15
> **rossmc92 said:**
> I am looking for something along the lines of Wine but a ppc version.not quite the same. There is nothing like that.

---

