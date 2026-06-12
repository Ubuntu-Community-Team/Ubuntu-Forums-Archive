---
title: "How do I roll back"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by javafiend on 2008-04-12
Since updates were run this morning, I haven't been able to run EQ2.  How do I "roll back" the updates and create restore points or backups before updates are run?

---

### Post by LaRoza on 2008-04-12
> **javafiend said:**
> Since updates were run this morning, I haven't been able to run EQ2.  How do I "roll back" the updates and create restore points or backups before updates are run?

First, find out how why it isn't running.

There is no way to undo updates.

---

### Post by essexboyracer on 2008-04-12
for future reference, you could image the hard disk with partimage or similar before applying updates or major changes to the system, that way if it all goes pear shaped you could just restore the HD image to a previous copy.

---

### Post by unutbu on 2008-04-12
Can't 
```
apt-get -f install packagename=versionnumber
```
be used to downgrade a package to an older version?

---

### Post by smartboyathome on 2008-04-12
> **unutbu said:**
> Can't 
```
apt-get -f install packagename=versionnumber
```
be used to downgrade a package to an older version?

It can, but that can also break other software.

---

### Post by javafiend on 2008-04-12
> **LaRoza said:**
> First, find out how why it isn't running.

There is no way to undo updates.

I've been trying to figure out why it isn't working.  I thought that if I could take it back to a previously working state, I could run the update manager and install one update at a time until it broke.  I can't say I'm at all familiar with the packages being installed and their individual functions, so about the best I can do is guess.

---

### Post by smartboyathome on 2008-04-12
Alt+F2 and run the program, checking the "Run in Terminal" icon. Post any output you get here.

---

