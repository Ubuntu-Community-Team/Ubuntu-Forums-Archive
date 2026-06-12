---
title: "Connecting two computers to the internet at the same time."
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by emnaki on 2008-01-03
My two computers, one  Windows and the other Ubuntu can't seem to connect to the internet at the same time when I plug them both into my broadband router. It works if both computers are Windows though. When I log in using windows, pppoeconf in Ubuntu does not detect a connection. Likewise when I log in with Ubuntu windows can't get a connection. So my question obviously is if there is a way to make both computers using different OS to log onto the internet at the same time.

---

### Post by eolson on 2008-01-03
It should work.  I do it all the time.  My router is a 2Wire but shouldn't make any difference.

---

### Post by emnaki on 2008-01-05
Well it doesn't for me, so what can I do about it?

---

### Post by Romin-1 on 2008-01-06
Two things you might try; boot the Ubuntu pc first and see if that works, and/or, make sure the Windows pc is idle, no net traffic, when you start Gutsy.

I have a 4 wire setup with 3 pc's and a printer and have never had a conflict.

HTH

Jon

---

### Post by ubutufan on 2008-01-06
The only possible reason i can think of is that you are using static IPs and both systems obtain the same IP. Check it.

---

