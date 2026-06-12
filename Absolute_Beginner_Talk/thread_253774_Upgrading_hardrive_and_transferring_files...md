---
title: "Upgrading hardrive and transferring files..?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by *Zebedee* on 2006-09-08
Good evening all :-)

I wish to move everything from my old 4gb hardrive to my new 10gb hardrive.
Can I just type cp-? c: d:   if I connect my new drive as slave??  
...Or is there a much better and safer way?

Many thanks in advance for your advice,
Regards, Zebedee

---

### Post by zxee on 2006-09-08
Take a look at man dd 
The syntax of dd is dd if=/dev/hda1 of=/dev/hdb1 of course your partition #'s will differ I've just provided an example, and in ubuntu you would of course preceed the dd command with sudo. Hope that helps.

---

