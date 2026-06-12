---
title: "HALP Powermac g4 install issues"
date: 2010-08-15
forum: Apple Hardware Users
---

### Post by TDLShow on 2010-08-15
Hello, and I am sorry if this has already been mentioned. I did search and I found nothing of the sort.

  I have an old powermac g4, that grey huge thing that is possibly bigger then I am. Well I'm tired of running Mac OS X 3.9 I cannot do anything with that. So I got myself a Ubuntu 6.06. Well I tried installing and it said it was not large enough. 
 
What?

I booted from CD is there anything I am not getting? I'd thank you forever if you help me with this small problem.

---

### Post by linuxopjemac on 2010-08-15
I don't exacttly know whay you did, but probably you try to install with the MacOSX still intact. You have to create space on your hard disk for Linux.

---

### Post by TDLShow on 2010-08-15
Oh. Thank you, but now there is this:

> No Newworld boot partition is found. The yaboot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS  Macintosh file system.

So I hit NO then I go through all that fun stuff. If I were to hit YES I would go all the way back to the partitioning menu.

So it goes to the Install yaboot on a harddisk. I do what it says.

SUDDENLY!

 > The installation of the yaboot loader failed.

Please check the system log or the output on the third consule (tty3).

WARNING: Your system may be unbootable!

I hit continue and then it fails. D:

---

### Post by linuxopjemac on 2010-08-16
You also need to make space for the yaboot boatloader.
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by shawnhcorey on 2010-08-16
> **TDLShow said:**
> So I got myself a Ubuntu 6.06. Well I tried installing and it said it was not large enough. 
 
What?

How much memory do you have?  When you boot from CD, a part of your RAM is used from RamDisks, so this may be what it's talking about.

---

