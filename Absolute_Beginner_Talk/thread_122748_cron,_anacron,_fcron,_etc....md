---
title: "cron, anacron, fcron, etc..."
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by DonQuixote on 2006-01-28
I have noticed that I have, for some reason, several cron applications installed.  I'm curious to know the differences between these, and if I need multiple applications of this type?

Thanks!

John

---

### Post by amohanty on 2006-01-28
Different apps to solve different dev itches... :) Welcome to FOSS..

---

### Post by TLE on 2006-11-21
Hey I used to wonder about this myself, so here we go with the simple explanation.

cron: It is the most simple one, it allows for you to schedule when a certain script is to be run. e.g. run "backup script" every Friday at 2000

anacron: It is basically like cron BUT it has the extra feature that it can check if something should have been run since the last time the computer was on. So if your computer wasn't on at Friday at 2000 and you turn it on at Saturday morning, then anacron will run the scripts then.

fcron: I don't exactly remember if fcron include the functionality of anacron. BUT it has the extra feature that it can run things at a certain interval of uptime. So you can tell it to run something every 5 hours your computer is on.

But so essentially it comes down to what amohanty said. Since they have different abilities the solve different assignments well. e.g. for the script that checks if any updates are available I would choose to put it in anacron, because that is the kind of assignment that you would want to run say once per day or as soon after as possible. Whereas something that backs up your documents it would perhaps make more sense to put it in a fcron script. Because you only build a need for backup when your computer is on and you edit your documents.

As for the second part of your question. "Do you need them?". Just leave them where they are, essential system processes depend on them so you don't want to try and mess with them, furthermore there is no need to, it is small applications that use only very little resources.
Regards TLE

---

### Post by DonQuixote on 2006-11-21
Hey!  Thanks so much for that explanation!

---

### Post by tgape on 2008-06-11
For posterity, anacron has a single schedule file, which does not include integrated capabilities to run jobs as other users (one can, of course, have a job invoke su, however.)  fcron provides a superset of capabilities - however, Debian developers have chosen to not fully utilize fcron's abilities, and instead choose to continue relying on cron, for some unknown reason.

fcron is bigger than cron which is bigger than anacron.  Anacron depends on having something run it; it doesn't run continuously.

(I found this thread while attempting to find out what that reasoning was.  At work, we've run systems for years just using fcron, and have not missed any functionality.)

---

