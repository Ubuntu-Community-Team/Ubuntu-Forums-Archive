---
title: "APT or Aptitude?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by bootslap on 2007-01-19
Just wondering if we should use sudo apt-get update or sudo aptitude update for updates? And what is the difference between the two commands?

---

### Post by igknighted on 2007-01-19
> **bootslap said:**
> Just wondering if we should use sudo apt-get update or sudo aptitude update for updates? And what is the difference between the two commands?

For updates there really is no difference as far as I know, the difference comes when installing.  Aptitude handles dependencies better than apt-get, and also keeps a log of installations (amongst other things).  I always use aptitude out of habit, but I suppose it really doesn't matter too much for updating sources.

---

### Post by tonyr1988 on 2007-01-19
Also, check out:

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Like igknighted, I also think there's no difference in the updates, just the installation / removal process.

---

### Post by mcduck on 2007-01-19
Well, since edgy there isn't even any real difference with installation/removal of software, as apt-get now has the autoremove feature. But I've had some problems with aptitude, after installing kde with 'aptitude install kubuntu-desktop' and 10 minutes of testing (without installing anything else) when I did 'aptitude remove kubuntu-desktop' it wanted to uninstall about half of my system.. So I stick to using apt-get. Never had any problems with it :)

---

### Post by Pobega on 2007-01-19
They really work the same, except aptitude removes all of the un needed libraries automatically while with apt-get you have to do "apt-get autoremove" to get rid of them.

---

### Post by riven0 on 2007-01-19
That's right! apt-get autoremove gets rid of the need for aptitude.

---

### Post by igknighted on 2007-01-19
Haha, the reason I use aptitude over apt-get?  I have small hands and find reaching for the hyphen key annoying.  In practice, the difference are usually trivial, so use whichever is more comfortable.

---

