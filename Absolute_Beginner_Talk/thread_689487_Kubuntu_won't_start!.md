---
title: "Kubuntu won't start!"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by feisty wookie on 2008-02-06
Hello all!

After just running my Kubuntu absolutely fine i am no longer able to start the windows manager. 

At startup i just get the blue Kubuntu screen with the load bar - and the load bar loads fully. 

Then the screen flickers quickly and goes straight to an empty Kubuntu screen with an empty load bar.

Then i get a totally black screen.

No commands do anything except for Ctrl + Alt + Del and Alt F1

Alt F1 allows me to log into my user but i still cant start my kubuntu/kde/kdm?

i tried "sudo dpkg-reconfigure kdm" like someone suggested but that didn't do anything.

I also tried "sudo dpkg-reconfigure xserver-xorg" and that gives me a blue screen that would help me set up my whole system as new. 

i really dont want to do this tho, since i dont actully know all the right configurations to use! but my kubuntu was running very nicely before.

is there any way that i could just revert to my previous settings or reconfigure using my previous settings? 

i am a total newbie.

im running kubuntu 7.04 on dell latitude d620. Nvidia Quadro nvs card.

thank you!

---

### Post by jaytek13 on 2008-02-06
What do you mean by "revert to the previous settings"? Did you do or install something before the desktop failed to load that you believe changed something to make it not work?

---

### Post by feisty wookie on 2008-02-06
No i didnt install anything. 

there is something to note though, adept manager did its usual updates and tried to update the ktorrent client - but it didn't update because it thought it would break the package.

---

### Post by jaytek13 on 2008-02-06
Can you get an error message from starting in recovery mode and then trying to startx or kdm?

---

### Post by feisty wookie on 2008-02-06
no, starting in recovery mode is exactly the same as starting in normal mode. it wont get to my login screen from recovery mode either.

---

### Post by LeslieL on 2008-02-13
I'm having exactly this problem, too. I had been running Kubuntu for days & installed a number of updates. Then Firefox hung for some reason so I restarted - or tried to. Got to the "initializing system services" stage of KDE starting, then reverted to first a black screen and finally a login screen. I log in and get to the system services stage again.

I checked permissions on my home folder - they're fine. Any ideas, anyone?

---

### Post by OffAxis on 2008-02-13
anything in the log files or dmesg?

```
less /etc/syslog
less /etc/Xorg.0.log
less /etc/kdm.log
dmesg | tail
```

(this wasn't quite answered before...)
does
```
startx
```

or 

```
kdm
```

do anything?

---

### Post by LeslieL on 2008-02-13
Thanks for the reply.

The most useful info seems to come from kdm.log. Here it is:
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 13 17:40:12 2008
(==) Using config file: "/etc/X11/xorg.conf"
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
Atom 4, CARD32 4, unsigned long 4
Synaptics Touchpad no synaptics event device found (checked 16 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0

Odd that it can't find the touchpad. The real problem seems to be related to the display, though. Any insights there?

---

