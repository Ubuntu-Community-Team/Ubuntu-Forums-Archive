---
title: "messed up again"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by charlier653 on 2006-07-16
was trying to enable my GeForce FX 5500, and was trying to follow the HOWTO. I must have skipped a step and now my X can't start.


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System: Linux 2.6.15.7 x86_64
Current Operating System: Linux charlie-desktop 2.6.15-26-amd64-k8 #1
SMP PREEMPT Fri Jul 7 19:43:47 UTC 2006 x86_64
               Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
               to make sure you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==)log file: "/var/log/Xorg.0.log", Time: Sun Jul 16 07:40:01 2006
(==) Using config file "/etc/X11/xorg.conf

how do i reconfigure from command line??

---

### Post by meborc on 2006-07-16
if i am not mistaken, the correct command to reconfigure is:```
sudo dpkg-reconfigure xserver-xorg
```

let us know how it went :)

---

### Post by h2gofast on 2006-07-16
everyone has done this once.
from now on before you edit your xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

This makes a backup copy. If you break your xorg.conf...
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
so you can look at your mistakes.  Then...
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
and you're good to restart X or reboot...

If you edited your xorg.conf incorrectly and restarted X without a backup
you get the commandline login.
Login with your user and password.
TWO options:
1. sudo dpkg-reconfigure xserver-xorg
this is the simplest way.  It "should" get you functioning again.
If your nvidia driver is installed wrong you can use the "nv" driver to get up and running.

2. If you want to do it yourself.
Login as above and...
sudo vim /etc/X11/xorg.conf
or...
sudo nano /etc/X11/xorg.conf

You might be more comfortable with nano.  As a sidenote:
If you are going to run linux, a lot of times it is easier to directly edit the config files than it is to use a gui.  Sometimes its your only option, so it can be very useful to learn a commandline editor.  emacs and vi are more popular and holy wars are fought by boys without girlfriends(or boyfriends) over which editor is superior.  Ignore them, just pick one and learn it because it's a handy tool to have.  here's a vim cheatsheet for starters.   [http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

cheers.

---

### Post by charlier653 on 2006-07-16
thank you both for the help! now have x back running:D :D ;) 

i tell you this learning curve can be extremely steep at times!

all my comp experience before now has been with windows, from 3.1 on.....my reason for coming to Ubuntu linux is NONE of windoze products are stable on my self built box.....constant hangs, and sometimes outright self reboot with no error message.](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by rbmorse on 2006-07-16
More often than not, when a computer spontaneously reboots the problem is in hardware.  I would suspect either an overheating CPU or an inadequate power supply.

---

### Post by charlier653 on 2006-07-16
have 450w power supply, and cpu core temp runs a steady 32 C.

was trying to run win XP pro x64.....ran win 98 ok without the spontaneous reboot.

after reboot, there would be a pop-up to send error report, most often said "unknown device driver". was probably ac97 for the realtek sound on the MB.

occasionally would be "video driver", with instructions to reduce the hardware acceleration. had that shut off completely, but still gave same error code......funny thing is, the actual stop codes when i researched them were totally unrelated to vid or sound, or anything else on my box.

---

### Post by charlier653 on 2006-07-24
found the freeze/spontaneous reboot culprit

bad mem stick

bought 2 512Mb sticks from an online distributor, BOTH turned out to be bad.

they will not honor their guarantee, which leads me to believe they KNEW they were sending "factory returns". 

if you need to know who these rippers are, just add "at gmail.com to my user name

---

