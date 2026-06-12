---
title: "output to the projector?"
date: 2007-07-13
forum: Apple Intel Users
---

### Post by tchorix on 2007-07-13
Hi guys,

Has anyone been able to get output to a projector in order to make presentations?

I can work with an external Mac screen, but for that I have to boot with the screen already plugged to the video output. But the projector refuses to work with the xserver. I can see the splash of ubuntu booting and shutting down. I can also see the consoles (Ctrl+Alt+F1..6), but I can't get any display of the desktop. I've tried different resolutions, but nothing... any ideas?

cheers
Tch

---

### Post by pveith on 2007-07-14
Is this the pro version? If not you should try the xserver-xorg-video-intel package inststead of the standard xserver-xorg-video-i810. The intel-package contains a newer driver, which works perfect for my macbook and the projectors here at the university.

---

### Post by cyberdork33 on 2007-07-14
What model machine you have, and what video device would be helpful.

---

### Post by tchorix on 2007-07-16
Hi pveith. Do you have to change the resolution of the computer to be able to project? or are you using dual screen? 

About the question of cyberdork33, I have a McBook Pro Intel Core Duo, first generation. The projector is a Dell, but that shouldn't matter very much, because the idea is to use it abroad, I won't be able to know in advance which projector will be available.

cheers and thanks for the replies
Tch

---

### Post by cyberdork33 on 2007-07-16
I meant the video card in your machine, but from what you posted, I assume it is the ATI X1600.

The fglrx drivers comes with a control panel. It is not included in a normal ubuntu install of the fglrx driver. I am pretty sure you can use it to configure a second screen.

If it is not available by itself in the repos, then you can download the driver from ATI's website and create Ubuntu deb files with it. then you can install the deb for the control panel.

---

### Post by pveith on 2007-07-17
I use clone-mode, which swiches the resolution to what the beamer supports. This is just logging off as my normal user, restart X and login again. I had to create a user for this, so that my taskbars are not shuffled everytime i use external display devices. But with clone mode i don't have to tell for instance open office impress, which screen it has to use. So for me it is a trade off. Not using xinerama enables me to use all programs as they are preconfigured.

I use a white macbook 2,16 GH with intel-graphicadapter.

(Oh i forgot to mention: i work at an university and presentation are my work. So i will struggle to get every possible beamer to work with my settings. Up to this time it just worked.)

---

### Post by tchorix on 2007-07-17
Ok... I will try these things at the end of this week, I'm away from the university some days, and I don't have a projector near by now to test.

cheers
Tchorix

---

### Post by pveith on 2007-07-17
Just use a normal monitor for testing, if available. If that works, you should have no probelms with projectors. The intel driver is quite good at detecting monitors and auto-configuring them. Initially i used a 17' Flat-screen to test secondary output and tried to configure the i810 package. As soon i switched to the intel package it just worked without me doing much config. Hope that helps.

---

### Post by cyberdork33 on 2007-07-17
> **pveith said:**
> Just use a normal monitor for testing, if available. If that works, you should have no probelms with projectors. The intel driver is quite good at detecting monitors and auto-configuring them. Initially i used a 17' Flat-screen to test secondary output and tried to configure the i810 package. As soon i switched to the intel package it just worked without me doing much config. Hope that helps.

Macbook Pro does not have Intel graphics (unless the rev1 did.)

---

### Post by tchorix on 2007-07-20
It still doesn't work. I tried with the xserver-video-intel instead, but I got a similar behaviour. I can see the consoles and the usplash for booting and shutting down, but nothing from xserver. I also installed the control panel of fglrx to be sure I was in clone mode.

The only thing that it works is plugin an external apple screen, and then reboot the xserver. Simply doing logout login does not rebooting, I have to do Ctrl+Alt+Backspace.

Do you still have ideas about what can I try?
cheers
Tch

---

