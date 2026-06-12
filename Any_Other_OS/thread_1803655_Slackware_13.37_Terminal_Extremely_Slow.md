---
title: "Slackware 13.37: Terminal Extremely Slow"
date: 2011-07-13
forum: Any Other OS
---

### Post by FormatSeize on 2011-07-13
I am running Slackware 13.37 with Xfce as the DE. The normal console works like normal. But when I go into the DE, the terminal is alarmingly slow. I'm not doing anything weird like timing builds and complaining about microseconds here. I'm talking basic things like ``cd'' and ``ls'' can take up to ***two minutes***(!). 
 
This is terrifying. At first, I thought it was something I did, or something, so I rebooted. Still happening. Then, when building a package (a reasonably small one) took over an hour, I couldn't take it anymore. I did a fresh install, but the problem persisted. 
 
Is anyone else having this happen, or something similar?
 
 
=================
Hardware
Dell GX270
Pentium 4 Single Core
1 Gig DDR RAM
40 Gig HDD
=================

---

### Post by sffvba[e0rt on 2011-07-14
Hi,

I didn't have any issues with 13.37... the hardware I was using is a bit better but if the hardware can handle a DE then is shouldn't have issues with a terminal... Best place to get good advice would be to try out Linuxquestions.org... the official Slackware forum is there.


404

---

### Post by andrew.46 on 2011-07-14
Hmmmmm..... I wonder if you need to disable compositing? Try adding the following to /etc/X11/xorg.conf:

```

Section "Extensions"
Option "Composite" "Disable"
EndSection

```

This worked with a similar situation on my own system.

---

### Post by FormatSeize on 2011-07-15
> **andrew.46 said:**
> Hmmmmm..... I wonder if you need to disable compositing? Try adding the following to /etc/X11/xorg.conf:

This worked. 
 
I had no idea that compositing would be enabled by default in Xcfe. I didn't know that it could have compositing being that its supposedly "cholesterol free".

---

### Post by andrew.46 on 2011-07-15
> **FormatSeize said:**
> This worked. 

Excellent news :).

 > **FormatSeize said:**
> I had no idea that compositing would be enabled by default in Xcfe. I didn't know that it could have compositing being that its supposedly "cholesterol free".

I have a deep suspicion that there will be a similar situation with xfce 4.8 which will be hitting -current soon enough...

---

