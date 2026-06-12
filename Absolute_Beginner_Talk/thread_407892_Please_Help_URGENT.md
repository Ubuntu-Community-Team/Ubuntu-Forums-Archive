---
title: "Please Help URGENT"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by AdrenalineJunkie on 2007-04-12
Hello World.

I have made such a nooby mistake and well i need some help.

I installed a game (uplink) under wine, and bla bla bla it didnt work, made everything "big" and when i restarted the computer, a blue screen with the following appeared;

> Failed To Start the XServer (your grapical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem?

<yes> <no>

I dont know what to do.

Is there a way to solve this problem?

Failing that, is there a way to somehow get my files back?

Thanks in advance people.

---

### Post by caffienefree on 2007-04-12
Please select "yes" and post the output.

---

### Post by AdrenalineJunkie on 2007-04-12
Module Loader Present

Markers:  (--) probed (**) config file (==) Default setting,
             (++) Command line (!!) Notice (II) Informal
             (WW) Warning (EE) Error (NI) Not Implimented (??) Unknown

(==) Log File: "var/log/Xorg.0.log", Time: Thu Apr 12 22:40:55 2007
(==) Using Config file: "/etc/X11/Xorg.conf"
(ww) fglrx: No matching device section for instance (BusID PCI:1:0:1) found
(ee) No Devices Detected.

Fatal Server Error:
No Screens Found.

---

### Post by x8668x on 2007-04-12
Try running Xorg -configure -a and follow the prompts.  Looks like you don't have a device specified for the monitor.  You will also be able to configure your driver and so on.

Good Luck.

---

### Post by AdrenalineJunkie on 2007-04-12
How would i go about doing that? 

sorry im really noobish.

---

### Post by annda on 2007-04-12
boot into recovery mode and run this command:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by AdrenalineJunkie on 2007-04-12
thank you so much.

Really appreciated.

Fixed =]

---

