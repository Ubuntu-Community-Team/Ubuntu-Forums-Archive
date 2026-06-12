---
title: "setup.py: not found when running democracy"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2007-05-09
Hello. I grabbed the dependencies for Democracy 0.9.5.3 and did a ./run.sh but it said setup.py: not found. What is that and how do i get it to work? Thanks!

---

### Post by nyxynyx on 2007-05-09
anyone?

---

### Post by nyxynyx on 2007-05-09
I cant seem to get past that stage! I cant use the repo because its for edgy and it gives wierd errors about mozilla-dev when I try to install it through spm...

---

### Post by aidanr on 2007-05-09
there is a feisty deb in universe, 0.9.2.1 i'm running it right now

what's the exact error you get installing through synaptic?

---

### Post by nyxynyx on 2007-05-09
In synaptic i see 0.9.5.1 and the rep im using is from [http://www.getdemocracy.com/downloads/ubuntu.php](http://www.getdemocracy.com/downloads/ubuntu.php) . The error i received is
> democracyplayer:
  Depends: python (<2.5) but 2.5.1~rc1-0ubuntu3 is to be installed
 Depends: mozilla-dev  but it is not installable
 Depends: mozilla-psm  but it is not installable


---

### Post by aidanr on 2007-05-09
in synaptic you can select democracyplayer and democracyplayer-data and go to package -> force version and select the feisty package

if you want to continue trying to compile, i'll point you [here]("https://lists.ubuntu.com/archives/ubuntu-motu/2007-March/001343.html")

afaik it should be working again when 0.9.6 hits

---

### Post by nyxynyx on 2007-05-10
Ok using the one feisty's repo works. Thanks!

---

### Post by aidanr on 2007-05-17
the latest svn now builds on feisty

[https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs)

---

