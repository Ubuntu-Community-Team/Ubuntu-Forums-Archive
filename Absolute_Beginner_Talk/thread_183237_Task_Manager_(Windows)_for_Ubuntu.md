---
title: "Task Manager (Windows) for Ubuntu?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Niranjan81 on 2006-05-27
Hi,
    is there something like a Task Manager for Ubuntu wherein I can see which all applications, programs are running in the background and stop any if I don't need. My laptop has become pretty slow n i am having a feeling that might be some shit process is running in the background which I don't need (had been to a couple of "seedy" websites n am having a feeling that I might have picked something up).Thanks!

---

### Post by Klaidas on 2006-05-27
Maybe ```
top
``` would do the trick? :)

---

### Post by mostwanted on 2006-05-27
It should be in either an Applications sub folder (think it is here in Breezy) or in System (where it is in Dapper).

---

### Post by mlind on 2006-05-27
for Gnome, there's gnome-system-monitor

located at System > Administration > System Monitor
(Dapper)

---

### Post by wolfiii on 2006-05-27
Look under 'system' -> 'system tools' (or administration, I don't know how is it exactly called in english), there is an entry 'systemmonitor' (or something simlar)

---

### Post by Niranjan81 on 2006-05-27
yeah got it! ... applications>system>system monitor.....but nothing seems to be there.... but still my lappie has become real slow....cud it be because i am installing some java stuff like Eclipse and azureus?

---

### Post by mlind on 2006-05-27
[QUOTE=Niranjan81]yeah got it! ... applications>system>system monitor.....but nothing seems to be there.... but still my lappie has become real slow....cud it be because i am installing some java stuff like Eclipse and azureus?[/QUOTE]

Installing new software that doesn't run as daemon shouldn't affect your system's
performance. Atleast if you're not running those memory greedy applications
simultaneously..

Watch the "Resources" tab on the System monitor. If something steals CPU time,
or hogs memory, then you've found your candidate. Then switch to "Processes"
tab and select "All Processes" from View menu.

You can disable unneeded services by installing BUM, but be careful with that.

Also, too small/big swap or low disk space may cause slow response time from
system.

---

