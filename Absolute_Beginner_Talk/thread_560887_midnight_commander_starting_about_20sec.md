---
title: "midnight commander starting about 20sec"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by sammael666 on 2007-09-26
hi,

yesterday i had to reboot my box (kubuntu ff). after it came up if i type mc in terminal, it just does nothing for about 20s, then starts mc. i tried purging it off the disk (rm -rf /etc/mc, rm -rf ~/.mc,apt-get remove mc) and installing it again, i tried compiling it from source - nothing works :confused:

anybody has an idea what could be going on?

---

### Post by jaakan on 2007-09-26
it loads in about 5 seconds on my P3-450Mhz/256mb ram Dell laptop but I'm running 7.10.
and a lower number on my 64bit desktop. 

Do you have anything running in the background? like DNETC, BIONIC, or something else?

what does "top" show in the terminal? is your harddrive very active? What kind of system are you running?

are other terminal apps or commands slow?

---

### Post by sammael666 on 2007-09-26
nothing else running (apart from usual processes), most cpu consuming is amarokapp which uses about 2%. when i try to run mc, nothing changes, no output to stdout or dmesg, no cpu utilization, no disk io, no nothing for ~20secs. then it just loads like nothing ever happened. it used to load in about 'immediately' secs. i am running a intel core duo @ 1867MHz,1Gb RAM, latest nvidia drivers (not nvidia-glx, original drivers from nvidia's site), latest linux-2.6.x-lowlatency kernel. i observe this behaviour disregard of KDE running or not. i am left completely baffled as to what may cause this. note that nothing has been changed prior to firrst observing this, no hw/sw changes - just a simple reboot.

any suggestions welcome, i'll get back here as soon as i return from work (sigh)

---

### Post by sammael666 on 2007-09-28
well, strangest thing - i noticed it has to do something with ndiswrapper. i am currently switching my isp so instead cable i'm using wifi connection to my friends router. while module ndiswrapper is loaded, mc is starting 20 secs. if i do modprobe -r ndiswrapper mc starts instantly. sadly my knowledge of linux isnt' so deep as to get me further into this problem or what may cause it. well as i have to use wifi connection now, i'll bear with it till i get connected to my new isp

---

