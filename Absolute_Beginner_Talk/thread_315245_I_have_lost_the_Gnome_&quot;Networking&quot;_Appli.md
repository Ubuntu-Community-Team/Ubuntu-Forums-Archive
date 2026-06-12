---
title: "I have lost the Gnome &quot;Networking&quot; Application."
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2006-12-08
Under "System > Administration" is a selection called "Networking."  This part of the Gnome desktop has quit working.  It quit right after I installed Wireshark.  Please note that I did not lose the icon from the menu; rather, when I select the Networking icon, the application crashes and a bug report is generated.

I have uninstalled Wireshark, and under Synaptic Package Manager I have done a reinstall of the Gnome-system-tools.  Neither effort restored my "Networking" application.

Any advice on how to restore this critical application?

---

### Post by scrooge_74 on 2006-12-08
try uninstalling the system tool and then install it again maybe it will help

if not you can always make your network changes from the command line :D

---

### Post by OldDogNewTricks on 2006-12-08
A complete uninstall of the system tool uninstalls the entire Gnome desktop.  I don't know enough about the command line to reinstall the desktop.

As for networking from the command line, that is my eventual goal, but I'm not ready to try it yet.  I've already seen that it is more efficient, more sure, and
very gratifying to use the command line.  BUT, it is a  huge learning curve to parse every command in one's mind. I greatly admire those who do it with ease.  I'm just not there yet.

---

### Post by scrooge_74 on 2006-12-08
if you uninstall your desktop you can always get it back from the command line using sudo apt-get install gnome-desktop

All you need to know to configure your card you can find it here [http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm)

have fun!!

---

