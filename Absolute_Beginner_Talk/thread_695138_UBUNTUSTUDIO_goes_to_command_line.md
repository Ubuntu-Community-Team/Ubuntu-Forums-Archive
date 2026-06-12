---
title: "UBUNTUSTUDIO goes to command line"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by kzman on 2008-02-12
I have recently purchased a PC to use as a LINUX machine.  It has an AMD64 X2 with 4 GIG Ram.

I wanted to use 64Studio but couldn't get internet access.

So I tried ubuntustudio 7 for AMD alternate.

When I boot up the PC, it goes to a command line.

I have never been able to get to a screen -- always black background with white letters.

I have tried a number of different suggestions like GMD and KMD and startx.  But either get errors or just nothing.

I tried to load UBUNTU 7 for AMD and it showed "UBUNTU" with a bar that kept moving but eventually just hung up.
Today I ran the disk check from the DVD and it indicated that 1 file error was detected.

Anyway, I would rather stay with ubuntustudio if I could just do something other than command line.

If anyone can help me, it would be great.

Thank you

---

### Post by taurus on 2008-02-12
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by kzman on 2008-02-12
Tried what you suggested.

It went for 3/4 of screen or so and then the following:

xauth:  creating new authority file /home/randy.serverauth.5016


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux randy 2.6.22-14-rt #1 SMP PREEMPT RT Sun Oct 14 22:53:32 GMT 2007 x86_64
Build Date: 29 September 2007
Module Loader present
(==_ Log file: "/var/log/Xorg.0.log", Time:Wed Feb 13 04:15:12 2008
(==) Using config file: "/etc/X11/xorg.conf"

No valid FontPath could be found.
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

Unfortunately, I cannot get to GUI to bring up e-mail or anything like that so cannot send you exactly what I see on that PC.  Sorry if I typed anything wrong

---

### Post by kzman on 2008-02-13
Tried what you suggested.

It went for 3/4 of screen or so and then the following:

xauth: creating new authority file /home/randy.serverauth.5016


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu
Current Operating System: Linux randy 2.6.22-14-rt #1 SMP PREEMPT RT Sun Oct 14 22:53:32 GMT 2007 x86_64
Build Date: 29 September 2007
Module Loader present
(==_ Log file: "/var/log/Xorg.0.log", Time:Wed Feb 13 04:15:12 2008
(==) Using config file: "/etc/X11/xorg.conf"

No valid FontPath could be found.
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

Unfortunately, I cannot get to GUI to bring up e-mail or anything like that so cannot send you exactly what I see on that PC. Sorry if I typed anything wrong

---

### Post by taurus on 2008-02-13
Run the command again except this time, skip the -phigh option.

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by kzman on 2008-02-13
ACTUALLY for my problem, I found the answer.

I cannot say that what you suggested did not help but here is what I had to do.

I found a command and modified it

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

sudo apt-get install ubuntustudio-desktop

(I modified from one I had that just showed ubuntu-desktop)

<<<   then I entered the next two commands >>>>

gdm
startx

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

I cannot remember if I had to do anything else but I believe this was it.

>>>>>>>>>>>>>>

And for my computer, I had to resize the screen area as the top part of the screen where you can select applications had been hidden.

---

