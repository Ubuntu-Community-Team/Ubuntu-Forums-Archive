---
title: "[SOLVED] White screen ubuntu will not start"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by jryprt on 2007-10-05
Hi all: Iam a noob OK here it is I had the same thing as this post
[http://ubuntuforums.org/showthread.php?t=561226](http://ubuntuforums.org/showthread.php?t=561226)
Failed to start X server (your graphical interface) I have tried
sudo dpkg-reconfigure xserver-xorg went through the setup rebooted got to log in got the yellow screen like it was starting ok then it went black and then got a white screen with a mouse pointer and thats it .
So I did a reinstall and rebooted and got to log in again yellow screen than black than white with mouse pointer . ubuntu will not start .
Please give easy to follow how to, I will need to print it . iam on xp to write this need to boot back and forth . I just put in the GeForce 6600
it works on xp . Thank You Jerry

Dell 4700
P4 3.20GHz HT
1GB ram
160GB HHD
GeForce 6600
XP + wubi ubuntu 7.04

---

### Post by Pumalite on 2007-10-05
So, did you try 'vesa'?.

---

### Post by jryprt on 2007-10-05
> **Pumalite said:**
> So, did you try 'vesa'?.


Where should I try 'vesa' when doing sudo dpkg-reconfigure xserver-xorg setup
Thanks Jerry

---

### Post by Pumalite on 2007-10-05
When they ask you for a driver. (vesa is a jack of all trades that allows you to get IN the system. Later you can download proprietary drivers, etc)

---

### Post by jryprt on 2007-10-05
I will boot in and try it , will be back to let you know 
Thanks Jerry

---

### Post by jryprt on 2007-10-05
Still the same white screen with mouse pointer. When I went thur setup it asked about xorg setup 
It choose bitmat is that right ?
Thanks Jerry

---

### Post by Pumalite on 2007-10-05
When it ask you if you want to review xorg you have to say no. That will take you to a command line where you can input sudo dpkg-reconfigure xserver-xorg. I would accept most defaults, including saying no to 'framebuffers', choose 'vesa' and at the end: startx

---

### Post by jryprt on 2007-10-05
> **Pumalite said:**
> When it ask you if you want to review xorg you have to say no. That will take you to a command line where you can input sudo dpkg-reconfigure xserver-xorg. I would accept most defaults, including saying no to 'framebuffers', choose 'vesa' and at the end: startx

Iam not getting the Failed to start X server (your graphical interface) anymore but get the  white screen & mouse pointer after I log in it give me the splash screen for ubuntu on yellow screen , then gos black then white . After I sudo dpkg-reconfigure xserver-xorg I go thur setup at the end I did  startx  & got

xauth: creating new authority file /home/jerry/.serverauth.7023
fatal server error:
server is already active for display8
if this server is no longer running, remove /tmp/.xo-lock
and start again

I can run the livecd ok 
Iam lost as what to do 
Thanks Jerry
I can get to the command line - ctrl+alt+f1 from the white screen

---

### Post by Pumalite on 2007-10-05
You apparently have an xserver running. You can do this at the moment of the message and at the command line:
sudo /etc/init.d/gdm stop, then apply: sudo dpkg-reconfigure xserver-xorg
If you have no command line:
Ctrl+Alt+F1 to get a command line.

---

### Post by jryprt on 2007-10-05
> **Pumalite said:**
> You apparently have an xserver running. You can do this at the moment of the message and at the command line:
sudo /etc/init.d/gdm stop, then apply: sudo dpkg-reconfigure xserver-xorg
If you have no command line:
Ctrl+Alt+F1 to get a command line.

Ok I did sudo /etc/init.d/gdm stop, then apply: sudo dpkg-reconfigure xserver-xorg went thur the setup again then did startx got a lined black & white screen no ubuntu so I did sudo /etc/init.d/gdm stop, then apply: sudo dpkg-reconfigure xserver-xorg  and did sudo reboot ang got white screen again ?

Thanks Jerry

---

### Post by Pumalite on 2007-10-05
It looks like you have more than an xserver problem. I would start from scratch with Alternate CD following this guide:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(I would also allow space in the hard drive, download iso and install)

---

### Post by jryprt on 2007-10-05
I uninstalled all files saved the iso installed again now I can start ubuntu 
Thanks for your help Jerry

---

### Post by Pumalite on 2007-10-05
You are welcome. I'm glad it finally worked for you.

---

