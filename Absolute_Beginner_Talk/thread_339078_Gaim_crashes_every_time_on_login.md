---
title: "Gaim crashes every time on login"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2007-01-15
Everytime I try to log in with my MSN account, Gaim crashes, and I mean every time.
Anyone else had this problem? It has never done this before. I am using Dapper.

---

### Post by Duppy on 2007-01-15
I also had this. I think I upgraded Gaim and I do not get it anymore.

---

### Post by Ben Sprinkle on 2007-01-15
Upgraded to what? I have the latest in the ubu repositories, but it's not the current. Do I get beta  or something?

---

### Post by Pobega on 2007-01-15
Gaim 1.5.0 used to do this on Windows, but not Linux. What version are you using, 1.5.0 or 2.0.0-3beta?

**Edit:** 1.5.0 actually still does this on Windows, I just tried it out myself.

---

### Post by Ben Sprinkle on 2007-01-15
1.5.1cvs

---

### Post by Pobega on 2007-01-15
Try this:

> sudo aptitude remove gaim
wget [http://optusnet.dl.sourceforge.net/sourceforge/gaim/gaim-1.5.0.tar.bz2](http://optusnet.dl.sourceforge.net/sourceforge/gaim/gaim-1.5.0.tar.bz2)
tar jxvf gaim-1.5.0.tar.bz2
cd gaim-1.5.0
sudo aptitude install build-essential checkinstall
sudo apt-get build-dep gaim
./configure
make
sudo checkinstall make install

---

### Post by Duppy on 2007-01-15
Yep im like a month new to Ubuntu, had GAIM hated it, it always crashed so I used kopete.

Then I updated GAIM to 2.00 beta (something)

Now it is ok :)

---

### Post by Ben Sprinkle on 2007-01-15
Must be something with libGtkSpell0.

---

