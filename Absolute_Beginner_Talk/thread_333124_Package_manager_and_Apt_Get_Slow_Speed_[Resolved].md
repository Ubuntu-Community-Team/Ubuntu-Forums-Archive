---
title: "Package manager and Apt Get Slow Speed [Resolved]"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by blull on 2007-01-06
I can't figure out why my updates are running so slow.  Doing about 1619B/s in Synaptic, but its not my connection because I can download over 1MB/s from a few other sites at the same time.  Is there a problem with the service apt-get or synaptic connect to at this point in time?

---

### Post by aysiu on 2007-01-07
Maybe you might want to try a different set of mirrors?

This link will help:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by blull on 2007-01-07
Ok, I am kind of new to this, But the source list created only shows the address that I am currently using.  How do I change to a different list?  Im out of Georgia in the US if that makes a difference.

---

### Post by taurus on 2007-01-07
I usually remove the **us.** in front of all the repos in /etc/apt/sources.list and get pretty good speed out of them...

---

### Post by blull on 2007-01-07
Thank you so much!  Removing the US solved the problem

---

### Post by taurus on 2007-01-07
So you get good speed too.  ;)

---

### Post by MkfIbK7a on 2007-01-07
by remonving us do you mean from in front of archive.ubuntu.org?
just want to be sure

---

### Post by aysiu on 2007-01-07
> **wert613 said:**
> by remonving us do you mean from in front of archive.ubuntu.org?
just want to be sure
Yes.

---

### Post by MkfIbK7a on 2007-01-07
ok thx thats what i needed to know:D

---

