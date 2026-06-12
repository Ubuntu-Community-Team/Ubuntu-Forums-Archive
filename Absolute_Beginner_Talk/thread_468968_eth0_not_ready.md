---
title: "eth0 not ready"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by mAkKoOo210 on 2007-06-09
Guys, I'm desperate.
I can't share my connection.
When I start Firestarter, it says "device eth0 not ready"
How can I make it work properly?

---

### Post by Eric_Jardas on 2007-06-10
How did you installed your modem ?
Are you sharing a connection or ?

---

### Post by mAkKoOo210 on 2007-06-11
Well, I use my eht0 device to connect to another computer in a Lan network. I solved this problem writing in the terminal:
> sudo ifconfig eth0 192.168.0.2
Doing this I can share my connection without any problem, BUT, every time I reboot Ubuntu, I have to re-write it, because it loses the configuration. 
Do you know how can I avoid this problem?

---

