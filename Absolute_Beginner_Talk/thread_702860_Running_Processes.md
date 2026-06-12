---
title: "Running Processes"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Nxion on 2008-02-20
How can I tell if a particular process is running ? I used to remember the command but I forgot it.

---

### Post by wolfen69 on 2008-02-20
system>admin>system monitor

---

### Post by laidback on 2008-02-20
Have a look at System>Administration>System Monitor>Processes for gui display.

---

### Post by adw on 2008-02-20
```
$ top
``` should do it for ya i think:)

---

### Post by jan quark on 2008-02-20
```
top
```
```
ps -A
```

---

### Post by herbster on 2008-02-20
Two of the more complete means of monitoring your processes would be gnome-system-monitor and htop. If you don't have htop I believe it's sudo apt-get install htop. Gnome-system-monitor is a GTK-based GUI app that is probably more user-friendly for most. Then click the Processes tab and you can see them there, kill them, etc.

---

### Post by Nxion on 2008-02-20
Thanks for your replies.

I know you can use the system monitor to look at the processes. But what I was referring to is a actual command you put in the terminal to look for a particular process. I know about "top" but that shows you ALL the processes running.

---

### Post by herbster on 2008-02-20
You can use:

```
ps aux grep | name
```

ie., I put firefox and it gives me this:

```
(dabox)~/installs$ ps aux | grep firefox
bobby    18326  0.0  0.0   4264  1424 ?        Ss   Feb19   0:00 /bin/sh /usr/bin/firefox
bobby    18330  0.0  0.0   4264  1440 ?        S    Feb19   0:00 /bin/sh /usr/lib/firefox-2.0.0.12/run-mozilla.sh /usr/lib/firefox-2.0.0.12/firefox-bin
bobby    18335  5.3  7.0 438124 237672 ?       SLl  Feb19  78:39 /usr/lib/firefox-2.0.0.12/firefox-bin
bobby    20209  0.0  0.0   3464   812 pts/2    S+   20:07   0:00 grep firefox
```

---

### Post by Nxion on 2008-02-20
THATS IT, Thats the command thanks !!

---

