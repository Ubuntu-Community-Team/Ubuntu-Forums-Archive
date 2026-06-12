---
title: "wifi issue"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Durden on 2007-07-19
Ok so I'm on a toshiba laptop, wifi works fine with wpa etc with either network manager or wicd. I've started using wicd now because network manger just doesn't cut it for me. Anyway, regardless of which network manager I use I lose my wireless connection and am unable to bring it up again after a suspend/hibernate. Sometimes I lift my lid and it works great, other times it won't work until I reboot. It's basically the only thing that's driving me nuts right now.

Wicd's system tray icon also doesn't update for me when my network comes up. Hope someone knows some work arounds for me. Thanks in advance.

* oh and btw it's using an intel 2200BG card and driver.

---

### Post by imdano on 2007-07-19
What version of wicd are you using?  Some earlier versions had problems with the tray breaking when resuming from suspend/hibernation.  The newest version (1.3.1) fixes this problem for the most part.  I've done my best to fix all the bugs that were causing crashes on resume, but there's still occasionally a problem where it crashes because dbus (which wicd relies on for communication between the tray and daemon) stops responding, but I don't think this is a bug in wicd, I think it's a problem with dbus itself.

When you lose connectivity after a resume, do commands like iwconfig and iwlist stop working?

---

### Post by ubanchaos on 2007-07-20
can u even get on the net

---

### Post by ubanchaos on 2007-07-20
mine does the same thing but i dont go into standby/hibernation mode i just shut it off

---

### Post by Durden on 2007-07-20
I was using the latest wicd, 1.3.1. I just put network-manager on so that I'd have a working tray icon again. Kinda important to me. I don't know really how to diagnose it if it's dbus. I'll just have to shutdown rather than suspend/hibernate like others. Thanks for the replies guys.

---

