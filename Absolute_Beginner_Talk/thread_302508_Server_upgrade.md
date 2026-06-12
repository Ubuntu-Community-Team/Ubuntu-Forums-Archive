---
title: "Server upgrade"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by nickburns on 2006-11-18
I have a server version of ubuntu up and running.  I don't understand how to get the updates to come down and install them.  For instance on my regular gnome desktop I get some orange square at the top that says 5 new updates are ready to install, I click on it and install the updates.  But on my server version, how do I know if there is updates available, and how do I install them? Is is automatic? Even possible?

---

### Post by adam.tropics on 2006-11-18
[http://www.ubuntuforums.org/showthread.php?t=302367]("http://www.ubuntuforums.org/showthread.php?t=302367")

---

### Post by bernied on 2006-11-18
apt-get update
- updates your records of available packages
apt-get upgrade
- upgrades all installed packages taht are updateable
Use:
apt-get -s upgrade
to see what would happen, without making it happen (s is simulate, I think)

---

### Post by bernied on 2006-11-18
guess I just like typing eh?

---

### Post by adam.tropics on 2006-11-18
oh that's funny! Good on ya' bernied.

---

### Post by nickburns on 2006-11-18
Thanks, I looked around for help, with no luck.  It looks like someone posted a thread at the same time I did.  Next time I have to search 5 seconds later.    :)

---

### Post by adam.tropics on 2006-11-18
and the same person answered it.....4 minutes later!

---

### Post by nickburns on 2006-11-18
Like I have posted before, this forum has the nicest people helping out. I know that I am a NooB, but thanks for the kind help.

---

