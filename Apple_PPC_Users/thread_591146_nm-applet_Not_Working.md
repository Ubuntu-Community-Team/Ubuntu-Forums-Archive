---
title: "nm-applet Not Working"
date: 2007-10-25
forum: Apple PPC Users
---

### Post by pyre on 2007-10-25
I recently did a fresh install of Gutsy (because I had some issues after upgrading from Fiesty).  Now my nm-applet won't work.  It says that it can't find any interfaces.  They do exist though.

My wireless automatically joins my 802.11b network, and the Ethernet shows up as eth0 if I run 'ifconfig -a'.  The GNOME netstatus applet (the one that runs on the gnome-panel, not in the systray) can see it and access it.

The nm-applet sits in the systray saying that it can't find any interfaces.  When I right click on it and select "manual configuration" it brings up a blank window (only a title bar and a blank box instead of window contents).

I haven't had a lot of time to troubleshoot the issue (Ubuntu installed over-night, and the issue was there this morning, but I'm at work now).  The only thing that I noticed odd was that GNOME was setup to run using x-session manager rather than gnome-session manager.  Is that something new?  Is that even related to NetworkManager?

---

### Post by stream303 on 2008-01-21
> **pyre said:**
> The nm-applet sits in the systray saying that it can't find any interfaces.  When I right click on it and select "manual configuration" it brings up a blank window (only a title bar and a blank box instead of window contents).

I'm not a big fan of Network Manager myself having gone through what you did on my G5 iMac, and a 100% cpu resource hog on my G4 iBook. :)

What you describe above is similar to when I wiped out my

**/etc/network/interfaces**

file by messing around with it.

I learned a lot from this:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

I have left network manager installed but deactivated on my G4, and on my G5 I needed to start/restart various things in the manager applet and the network prefs.

---

