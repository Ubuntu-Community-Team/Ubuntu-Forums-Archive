---
title: "Trying to install wine"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by Chrissie on 2006-01-29
unfortunately whether I choose apt-get or synaptic, I get the message "Server unavailable". What now? Should I just try again later/tomorrow?

---

### Post by psomas on 2006-01-29
try again later...
i imagine that the server that hosts the package is down...

---

### Post by Chrissie on 2006-01-29
Fair enough. Will keep on trying.
Thanks

---

### Post by mgmiller on 2006-01-29
You will have much better luck with the newest version of wine.  I tried and didn't like the older wine that was available from the stock repositories.  You should add the following to your /etc/apt/sources.list

First make a backup
sudo cp /etc/apt/sources.list /etc/apt/sources.backup

then edit the file
sudo gedit /etc/apt/sources.list

and add the following 3 lines to the bottom:

## The wine sources
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/


Finally, you need to sudo apt-get update or, within synaptic package manager, click on the reload button.  Then search for wine.  You only need to install the entry called "wine"  The current version is 0.9.6-winehq-1


These are the repositories for the wine project and they work perfectly in ubuntu 5.10.  Also as they update wine, you will get automatic notifications and installs of the updates direct from the wine project.

You may want to go to:  [http://www.winehq.org/](http://www.winehq.org/)  and read about how to configure and install stuff.  It's not hard and I have DVDshrink, for example, working perfectly this way.  The basic way to get into the wine config after it's installed is to hit ALT/F2 and then type winecfg in the box at the top.  This opens the wine interface and lets you install and configure stuff.

Good luck and Happy Ubuntuing!

---

### Post by Chrissie on 2006-01-30
Tonight apt-get was available and I was able to install wine.
I even managed to launch the installer for startcraft, and the installation completed but with tonnes of error - I could see the error lines appear on the terminal as the windoz installer was processing.
Now what?

I'd like to remove/uninstall starcraft, and maybe try with a game that does not require to have the disk in the CD-rom reader, as this seem to be the problem. How to I uninstall?

---

