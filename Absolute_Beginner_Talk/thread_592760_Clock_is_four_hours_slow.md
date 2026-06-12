---
title: "Clock is four hours slow"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-10-26
When I installed Gutsy, I selected my time zone (New York); I've never had problems before, but all of a sudden, I do. My BIOS time is set correctly, but my clock is four hours behind (NY time is GMT -4). I can use UTC and the clock works, but my Pidgin timestamp, for instance, is still four hours off. Any ideas how I can fix this? Thanks.

---

### Post by oldos2er on 2007-10-26
If you mean the clock in Gnome top panel, right-click on it and choose 'Adjust date and time.'

---

### Post by edwardLS on 2007-10-26
I had trouble with this very issue back in Dapper Drake days.  I received some help from this forum, and it fixed my problem, but I am not sure why.  In any case, I will pass it along to you.

Find the file /etc/default/rcS and 'sudo gedit'  that file.  In that file fine a line that looks like:

UTC=yes.

Edit that to UTC=no

Hope this will help.  Good luck.

---

### Post by nymphaeles on 2007-10-26
how about auto update the clock with ntp?  That should help.

---

