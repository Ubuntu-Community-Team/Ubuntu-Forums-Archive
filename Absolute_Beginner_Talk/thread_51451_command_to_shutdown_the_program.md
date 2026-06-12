---
title: "command to shutdown the program"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2005-07-24
Ok, i want to shut xmms as it is malfunctioning... how should i go about it? what is the command in the terminal..

---

### Post by ubuntp on 2005-07-24
killall xmms

and if that doesn't work then find the PID of xmms by using:

ps ax | grep xmms
kill -9 PID_NUMBER

---

### Post by KrisDwyer on 2005-07-24
[QUOTE=ubuntp]killall xmms

and if that doesn't work then find the PID of xmms by using:

ps ax | grep xmms
kill -9 PID_NUMBER[/QUOTE]
 thanks, the killall command work... and i am indebted... (Stupid Schnappi the Krokodil!)

---

