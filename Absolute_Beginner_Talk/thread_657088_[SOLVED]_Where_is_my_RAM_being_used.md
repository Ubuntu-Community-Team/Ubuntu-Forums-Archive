---
title: "[SOLVED] Where is my RAM being used?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mfk on 2008-01-03
I have 2 x 1Gb RAM chips in my pc. The computer reads it and displays that I have 2 gigs. But if I look in task manager there are only a couple of programs running at this moment I am running Avidemux, it's taking up 25mgb but it says that it's taking 80% of my RAM. I don't get it.  I ran the ```
 free -m
``` and then I ran ```
vmstat
```. Here it showed me that I am actually somehow using 100% of my RAM. COuld someone explain this to me.:?:

---

### Post by ukripper on 2008-01-03
Avidemux is resource intensive application as it is encoding it will take most of the CPU if in Above average mode

It is not taking 86% RAM. it is taking 86% CPU usage

---

### Post by Fixman on 2008-01-03
Compiz fusion (the program that does all those nice effects) generally uses most of your avalible RAM, witch is not a problem since it unloads it quickly when another program starts.

---

### Post by stump138 on 2008-01-03
You're jsut seeing it wrong as there can be a bit of confusion in how it displays :)  According to your picture you're actually using 298 meg with 1665 free, Look at the -/+ buffers line for the actual usage:)

---

### Post by PmDematagoda on 2008-01-03
As stump138 stated, you are really using only 298Mb of RAM for the programs and processes, the other part is also seen as being in use but it is the cache which in reality is like a sort of "emergency store" of RAM to be used in situations where RAM is needed quickly and also helps in improving the speed of Ubuntu.

---

### Post by lswest on 2008-01-03
also, the 86% is using the CPU, not the RAM.  ah, didnt realise someone said this already:P

---

### Post by mfk on 2008-01-03
Yeah I'm a dumbass...didn't sleep last night so yeah...I...thanx anyhow :).....preciate your quick responses.

---

