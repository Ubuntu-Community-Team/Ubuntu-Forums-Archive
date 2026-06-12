---
title: "No System Logs!"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by dpack on 2006-07-21
I've done a clean install of Dapper Drake. Since the day of the installation, if I go to System > Administration > System Log I have NO logs! I have nothing more than a white screen no matter what date I pick for the past week. I went to System > Administration > Services and Computer Activity Logger (klogd and Sysklogd) are checked. What am I missing?

---

### Post by SkyNet2029 on 2006-07-21
kind of a silly question, but are they listed as 'running'?
if not click on 'administrator mode' and fire them up.

When you (Ctrl+Alt+F8 ) do you see where the starup script lists

* STARTING system log
* STARTING kernel log 
this should be a little after it lists what runmode you just entered.

---

### Post by A2A on 2006-07-21
dpack,
You have to point the application to the log source (/var/log)
So go to System -> Administration -> System Log
Once inside System Log, click on Log -> Open, then browse to /var/log and all the logs you ever need are there :-P

Hope this helps,

A2A

---

### Post by dpack on 2006-07-22
> **A2A said:**
> dpack,
You have to point the application to the log source (/var/log)
So go to System -> Administration -> System Log
Once inside System Log, click on Log -> Open, then browse to /var/log and all the logs you ever need are there :-P

Hope this helps,

A2A

Thanks! That got it. In Breezy all the logs were already opened. When I went to Open it defaulted to /var/log and all I had to do was select the logs modified Today to see what I needed.

---

### Post by A2A on 2006-07-22
Glad I could help :p

Cheers!

A2A

---

