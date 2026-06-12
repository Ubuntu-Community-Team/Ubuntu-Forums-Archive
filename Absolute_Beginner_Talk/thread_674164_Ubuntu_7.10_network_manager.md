---
title: "Ubuntu 7.10 network manager"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Jaack on 2008-01-21
Hi, I have recently installed Ubuntu 7.10, but it won't let me setup a wireless connection to my router. I have partitioned the drive and the other OS is windows vista which i have an internet connection on. I have tried to setup my internet manually but it still won't work, my router hasn't been recognised by Ubuntu and isn't even shown in the list of choices.
So if anyone knows the reason why my wireless refuses to work on Ubuntu please help.:confused:
Thanks

---

### Post by Vadi on 2008-01-21
Do any routers show up in the list? (when you left-click on the little applet top-left)

Also, open up the terminal (applications - accesories - terminal), and copy/paste this in there:
```
iwconfig
```

What does that produce?

---

### Post by Jaack on 2008-01-21
I typed it in and this is what came up:

jack@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I'm not sure what it means so if you could help.
Thanks

---

### Post by Jaack on 2008-01-21
sorry about those smilies I didn't think they would come up! :confused:

---

### Post by Vadi on 2008-01-21
Bad news: You have the card with the worst possible linux support!

Good news: because it's so bad, there has been a ton of work on it to get it working..

First off, in system - administration - restricted drivers, is the wireless driver in use?

---

### Post by Jaack on 2008-01-21
I have a driver in their but it is not in use and when I try to enable it this error message appears.

The software source for the package

   nvidia-glx-new

 is not enabled



Also is their any other versions of Linux that work properly or work better with my card?
Thanks

---

### Post by Vadi on 2008-01-21
This isn't a Ubuntu problem really but a configuration one.

I think I know what's wrong though; go to System - Administration - Software Sources. Disable the CD, and the "Source Code", and check off everything else. And then try enabling the wireless driver again.

---

### Post by rosegarden78 on 2008-01-21
a) Install the BCM43xx package from the repos

b) Type
sudo modprobe bcm43xx
from a terminal

c) Type
nm-applet
from a terminal

Note: if nm-applet is missing check the repos.  You can run nm-applet even without a dock in Blackbox, fluxbox and xfce but it works better if you run Nautilus and Kicker.

---

