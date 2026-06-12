---
title: "How to open Desktop"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by smohamedfarouk on 2008-03-01
Hello Friends
I am in ubuntu black screen (Shell screen), How to open desktop

I am in my shell prompt how to go to the desktop.?

Please help

---

### Post by mikeyphi on 2008-03-01
> **smohamedfarouk said:**
> Hello Friends
I am in ubuntu black screen (Shell screen), How to open desktop

I am in my shell prompt how to go to the desktop.?

Please help

Command:

startx



Post result!

---

### Post by banewman on 2008-03-01
Type - startx
and see if that gets you there.

---

### Post by smohamedfarouk on 2008-03-01
Please help this is what I get when i type startx from command shell

X Window System version 1.3.0
Release date: 19 April 2007
X Protocol Version 11. Revision 0, Release 1.3
Build Operating system: Linux Ubuntu (Xorg-server 2:1.3.0.0.dsg-12unbuntuu8)
Current Operating system: Linux farouk-desktop 2.6.22-14-generic #1 SMP

Module loader present
Markers: (--_ probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) information).

(==) Log file: "/var/log/Xorg.0.log" 
Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected


Fatal Screen Error: 
no screens found
XI0: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

---

### Post by PmDematagoda on 2008-03-01
Execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then try:-
```
startx
```

---

### Post by smohamedfarouk on 2008-03-01
What is the chipeset and what screen resolutions we have to choose?

Sorry to ask so many questions?

---

### Post by mikeyphi on 2008-03-01
> **smohamedfarouk said:**
> What is the chipeset and what screen resolutions we have to choose?

Sorry to ask so many questions?

During the reconfigure process - accept the default answer each time if you are unsure - it can be changed later when the desktop is working!

---

### Post by smohamedfarouk on 2008-03-01
I am having ubuntu inside virtual box.

Ubuntu appears inside virtual box with desktop only inside a small window of virtual box. even on full screen mode ubuntu appears only in the middle like a small window.

please can you tell me what to do to get full screen of ubuntu?

---

### Post by mikeyphi on 2008-03-01
Close the terminal window.
Open System/Administration/Screens and Graphics
- you should be able to set a suitable screen and resolution from the menu.

---

### Post by smohamedfarouk on 2008-03-01
Thanks for your help, I am there, except dont know what is the right configuration for screen resolution. I am better than before vertically i have covered the screen horiontally still some more  missing in both sides

---

