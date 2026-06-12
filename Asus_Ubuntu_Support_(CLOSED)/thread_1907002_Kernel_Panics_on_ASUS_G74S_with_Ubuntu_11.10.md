---
title: "Kernel Panics on ASUS G74S with Ubuntu 11.10"
date: 2012-01-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by timtaves on 2012-01-10
Hey there, I just got an ASUS G74S laptop.  I installed ubuntu 11.10 on it and now it is crashing about once per day.  When it crashes the screen just freezes and the caps lock button blinks.  I think this is called a kernel panic.  When it happens I have to use the physical on/off switch to turn it off and then back on.

From looking at forums it seems that other people have fixed this (on different computers) by turning off their wireless connection and the typing:  

sudo iwconfig wlan0 power off

into the terminal (I use wlan1).  This helps quite a bit but now I get kernel panics about once or twice per week instead of once or twice per day.  This is still a big problem for me as I need to run c++ simulations which take ~week to run.  

Any ideas?  Some of my specs are below.  Thanks in advance.

i7 - 2670QM - 2.2GHz
750GB HD+120GB SSHD (My OS is on the 120GB SSHD.  The system doesn't use RAID.)
I upgraded this from two 750GB HDs.
16GB of RAM - upgraded from 12GB.

---

### Post by gillza on 2012-02-13
I have G73sx-a1 laptop with 11.04 on it. I experience the same issue as you are describing. I have noticed that this happens most often when I unplug the laptop from power and use the battery and than plug it back in. As soon as 30 minutes later it goes into kernel panic. After shutdown and start it may go into kernel panic as soon as I log in. It may crash few more times while on power and slowly "stabilizes". I have no idea what is the issue. Inspecting the logs does not show anything worth noting.

---

### Post by timtaves on 2012-02-13
I have also noticed that once it panics it is more likely to panic again soon.  The logs also tell me nothing.

Just to give you an update as to what I have tried so far:

1. I put in a different HD (the one that the computer came with which still had windows on it) and ran Windows.  Instead of flat out crashing it restarts the computer some times.  I think it happens if I leave it with out using it for too long.  There is then an error message that just says some thing like 'Windows stopped working properly and had to restart'.

2. I tried running Ubuntu 10.10 off of a memory stick.  It still crashes.

3. I ran my HD, with Ubuntu 11.10 via my usb port.  It still crashes.

4. I installed the Wubi along side windows and that crashed too.

I'm starting to think that this is either a hardware problem or a problem with drivers.  If I can't figure it out in the next few days I will take it back (I bought the in store warranty) and get them to check the hardware.

I'll let you know if I find out any thing interesting.  Please also let me know if you do.

---

### Post by gillza on 2012-02-13
I haven't tried running windows for a while but I have noticed that the crashes in Ubuntu started around the same time as I have started to try and figure out "slow wireless" issue with ath9k drivers.
In addition I have tried running debian live cd for 24 hours with no issues. Actually I'm making a backup of my files to install debian instead of Ubuntu.

In Addition: Win7 does not crash. It is software related in my case.

P.S. When I run memtest it freezes. However, memory check in windows passed.

---

### Post by timtaves on 2012-03-07
Hey there, I think that I may have solved the problem.  When I bought this thing I asked them to put in an extra 4GB of RAM.  I opened it up and noticed that it was a different name brand than the other RAM in the computer.  I took it out and it has been stable for 4.5 days.  I suppose this could be a coincidence but I doubt it.

---

