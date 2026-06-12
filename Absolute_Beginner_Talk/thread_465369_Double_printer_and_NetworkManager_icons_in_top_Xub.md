---
title: "Double printer and NetworkManager icons in top Xubuntu panel!"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-06-05
Hi, I'm using Xubuntu 7.04 and have this problem all of a sudden:
In the top panel the icons for NetworkManager Applet and Printer Properties are now double, and I can't print anymore -- all printjobs are automatically paused and don't come out.
I haven't changed anything in the system, so I don't know why this has come about.
How do I get rid of the Doppelgänger icons?  Please help!

---

### Post by Blofeld on 2007-06-05
The printer icons appear to be instances of the Print Queue Applet.

---

### Post by Blofeld on 2007-06-05
I managed to get rid of the superfluous printer icon by disabling Xfce Menu > Settings > Autostarted Applications > Print queue applet (system tray icon) and rebooting.
Now for the Network Manager Applet icon!

---

### Post by Blofeld on 2007-06-05
PS:  printing works fine now.

I have tried disabling networking in one of the Network Manager Applet applets, but then both applets simultaneously disconnect me from the applet.

---

### Post by ugm6hr on 2007-06-05
Try reading this re: Network Manager
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

The last few entries solve the multiple icon issue.

---

### Post by Blofeld on 2007-06-05
Yes, it worked!
Thank you, ugm (if you don't mind me calling you that)!:KS
:popcorn:

---

### Post by ugm6hr on 2007-06-06
> **Blofeld said:**
> Yes, it worked!
Thank you, ugm (if you don't mind me calling you that)!:KS
:popcorn:

No worries.  Glad to pass it on.

---

### Post by Blofeld on 2007-06-06
Quick 101 tutorial:  getting rid of multiple printer and networking icons in Xfce (Xubuntu) system panel (the bit at the top right corner of the desktop):
* PRINTER ICON:  disable in "Xfce Menu > Settings > Autostarted applications" the "Print queue applet" and reboot.  There should only be one printer icon in the system panel now.
* NETWORKING ICON:  uninstall "NetworkManager Applet" in "Add/Remove Applications" or "Gnome Network Manager" in "Synaptic", reboot, reinstall, reboot.  There should now be no networking icon in the system panel.  Go to "Xfce Menu > Settings > Autostarted applications" and add "nm-applet --sm-disable" (the latter stands for "disable session manager"), and reboot.
And voilà, Bob's your uncle.

---

