---
title: "Show what programs are running?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2006-12-13
Ok, am i correct in saying that "/etc/init.d" is the equivalent to what services you have running in windows?

if this is true, what tells you what programs are running? for example, i closed my VLC Media Player window, but the music continued to play... how could i tell if the program was still running and kill it so it stops?

thanks!

Xubuntu 6.06

---

### Post by Dusty545 on 2006-12-13
To get a similar window to the Task Manager in W*ndows, click:

System-> Administration -> System Monitor

This will show the services that are currently running, the CPU usage, etc.

I've had this problem with VLC too (I use it for all A/V media playback) and have found that reopening it and then closing it stops it from playing.

I don't know if it's a bug or not but I'm going to report it.

---

### Post by 23meg on 2006-12-13
/etc/init.d is where your startup scripts are. Common ways of seeing running processes are ```
top
```and ```
ps aux
``` See the manual pages of top and ps for more information. ```
man top
``````
man ps
```

---

### Post by RMorris78 on 2006-12-13
thanks for the quick responses!!!

---

### Post by hyper_ch on 2006-12-13
Or if you are looking for a specific thing (and how often it's being run):

```

ps aux | grep apache

```
(for apache - just replace apache with the name of the app that you want to check)

---

