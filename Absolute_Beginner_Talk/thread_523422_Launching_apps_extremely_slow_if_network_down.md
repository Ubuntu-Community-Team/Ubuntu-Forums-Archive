---
title: "Launching apps extremely slow if network down?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Tsu Dho Nimh on 2007-08-11
Apps such as the screenshot maker, terminal, and notepad that have no reason to need a live internet connection are suddenly extremely slow to launch without one. They eventually launch, but the little spinner runs for 10-30 seconds.  Other apps as well are having issues ... OpenOffice, graphics viewers, etc. 

I have been accepting updates as they appear ... has something buggy been introduced? 

I haven't a clue where ot start looking for this problem.

---

### Post by Tsu Dho Nimh on 2007-08-11
I tried one remedy, which was editing the hosts file, and it did not good.  The slow launching persists unless the computer is connected to the network. 

Code:
127.0.0.1       localhost
127.0.1.1       computername

I added my hostname to the first line as suggested:

Code:
127.0.0.1       localhost computername
127.0.1.1       computername

---

