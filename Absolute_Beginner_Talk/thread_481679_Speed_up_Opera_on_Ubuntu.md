---
title: "Speed up Opera on Ubuntu"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-06-22
I am not sure what the problem is that Opera seems to work badly on my Ubuntu installation. Flock runs fine so does Firefox... 

Any tips on optimizing opera on ubuntu? System is P4 1.8 with 1 Gig RAM.

---

### Post by Crafty Kisses on 2007-06-22
> **Sushubh said:**
> I am not sure what the problem is that Opera seems to work badly on my Ubuntu installation. Flock runs fine so does Firefox... 

Any tips on optimizing opera on ubuntu? System is P4 1.8 with 1 Gig RAM.

Not sure about Opera. Opera itself is already pretty optimized. Although there is a optimized version of FireFox called "SwiftFox".

---

### Post by kerry_s on 2007-06-22
a bit cryptic, how about giving specific details on the problem so we know were to start.
loading speed can't be helped. browsing there are a few settings you can play with.

---

### Post by Sushubh on 2007-06-22
switching from one tab to another is jerky... the browser just sucks on digg.com... it becomes sluggish after a while... :)

for firefox... flock is damn responsive...

maybe it's becoz opera uses its own UI manager i guess... a future version of Opera is due to support QT4. how would that affect the performance of opera on linux?

---

### Post by Happy_Man on 2007-06-22
> **Sushubh said:**
> switching from one tab to another is jerky... the browser just sucks on digg.com... it becomes sluggish after a while... :)

for firefox... flock is damn responsive...

maybe it's becoz opera uses its own UI manager i guess... a future version of Opera is due to support QT4. how would that affect the performance of opera on linux?
If you use KDE, Opera will become your browser of choice. If not... well, it won't be much different.

---

### Post by Sushubh on 2007-06-22
umm. u mean to say that opera is likely to be more responsive in kde? if that is the case i can move to kde from gnome! 

smooth opera is essential to my online life... anything for it mate. :)

---

### Post by kerry_s on 2007-06-23
slugish and jerky ui is usually problems with the vid card. what vid card do you have and what driver is it using.

gedit /etc/X11/xorg.conf

right click select all and paste it here, so we can look at.

also while your at it that's have a look at your log for errors.

gedit /var/log/Xorg.0.log

copy and paste here

---

