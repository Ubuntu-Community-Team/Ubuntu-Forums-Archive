---
title: "I am in BIG trouble, please help... [chmod related]"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Ionix on 2006-12-19
Hi

I am a 2 weeks experience linux user... And just now i have screwed up my company server by typing the followings.

chown root -R /var/*
chgrp company -R /var/*
chmod 777 -R /var/*

I thought of resetting everything, then slowly rebuild the permission. BUT I NEVER EXPECT it'll SCREW THIS UP...

now my whole /var is 'opened' I cannot chmod 770 -R /var/lib/* cause this will basically screw up my joomla installed on apache...

So I really hope anyone here can help me out, and hopefully rebuild the permission to a more secure state than 777 to all...

Urgently... My boss is back tomorrow

---

### Post by Ecthelion on 2006-12-19
I have done this myself once and believe me, there is only one solution:
Reinstalling your computer.
That 'll be faster than looking up all the permissions, which is anyway something you'll never get done by tomorrow.

Just remember never to use chmod -R for anything that isn't your own personal stuff
Best is never to use it at all.

---

### Post by xyz on 2006-12-19
You may also want to go over your file permission chapter:
[FilePermissions]("http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&zu=https%3A%2F%2Fwiki.ubuntu.com%2FFilePermissions")
Good luck.

---

