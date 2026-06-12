---
title: "Installing from .tar.gz (Firefox 2)"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-16
So, I've got the .tar.gz of firefox 2 downloaded, and I extracted the folder to my home folder.

How do I install the file ... ?

I tried ./configure , make, and sudo make install , but no luck

---

### Post by taurus on 2007-01-16
It's already a binary so you don't have to build it.  Just extract to where you want to install it (maybe like /opt) and run from it.  Perhaps this would help!

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by highneko on 2007-01-16
Probably the file "run-mozilla.sh". Type "./run-mozilla.sh".

---

### Post by kbsuperstar on 2007-01-16
Didn't work :( 

Any other suggestions?

---

### Post by kbsuperstar on 2007-01-16
Nevermind. I found a script in the folder I extracted, ha. Thanks

---

### Post by taurus on 2007-01-16
> **kbsuperstar said:**
> Didn't work :( 

Any other suggestions?

And what didn't work!  What is the name of the file that you just downloaded?

---

### Post by kbsuperstar on 2007-01-16
I just googled Firefox 2 and got it from the mozilla site.

---

### Post by taurus on 2007-01-16
So you finally get it to run, right?

---

### Post by NeoLithium on 2007-01-16
One thing I've noticed from those who download the tarball from firefox, extract it into their /home/USER directory; I guess since thanks to firefox's lack of instuctions ;)

The best way to install that file, to overwrite your firefox 1.5x is to move it into /usr/lib before you extract it, then bingo; firefox is overwritten with the new version, of course all your bookmarks, etc are stil in place :)

---

