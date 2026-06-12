---
title: "Bootscripts"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by Rizado on 2005-11-12
Hi

I have just installed firehol and now I want it to autostart at boot time. Firehol is a script in /etc/init.d/ so I tried to make a link in /etc/rcS.d called S70firehol but it doesn't work. Also as it's going to be used as a nat router how do I turn X and alsa and other unnececary services off? I'm new to both ubuntu and debian but i've used slackware and fedora and some other distros before so I know how to navigate through linux.

BTW the computer is a PowerMac G4.

---

### Post by jorn on 2005-11-12
Hi!
You must go: System>indstilliger(danish)>sessions: Started programs>add.
Here you must either enter the name of the program or find its startscript. Maybe in /usr/bin. This is what I now. Good luck.
Jørn

---

### Post by apjone on 2005-11-12
If it is just going to be a NAT router , not a desktop machine maybe it would be best just installing the server edition of ubuntu instead of the full works

---

### Post by teaker1s on 2005-11-12
sudo update-rc.d foobar start 20 2 3 4 5 . stop 20 0 1 6 .
will start foobar in /etc/init.d across system thats how I run my script to set keys the kernel doesn't know on my keyboard

---

### Post by teaker1s on 2005-11-12
and to remove 
sudo update-rc.d -f foobar remove

---

### Post by Rizado on 2005-11-14
I got it working now. I just reinstalled and it complained something that firehol wasn't allowed to start because of a config file (And a link to the file) I just changed it to allow, downloaded bum and set the start order. Everything works great.
Also I think I'm gonna let X be on. It doesn't use much CPU anyway and it's nice to have running. It's amazing how nice ubuntu run on a 466mhz. I have 512mb ram though, but still.

Server edition of ubuntu? What's that and where to get it?

---

