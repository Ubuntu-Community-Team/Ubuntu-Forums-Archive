---
title: "Issues after updating"
date: 2008-06-21
forum: Apple Hardware Users
---

### Post by ericks13 on 2008-06-21
I finally got everything working how I wanted just now and I got an alert for a software update.  I chose to download and install everything and it required a restart after it finished installing.  Understandable.  I've rebooted to it three times now, and each time after logging in I get a white screen where only my mouse is seen.  No keyboard commands work or nothing.  The only way to get out of it is to do a manual shut down.  No error messages came up while it was downloading the updates, so what gives?  I'm running on a triple-booting iMac and everything was fine before the updates.

---

### Post by cyberdork33 on 2008-06-23
it sounds like you have not installed the proprietary ATI driver (or not updated it) and the system is trying to start compiz which will not work. 

You should be able to (blindly) login, wait a couple of minutes for everything to startup, then do ALT+F2 to bring up the run box and type "metacity --replace" and you will see the desktop. Otherwise you can start in recovery mode and do everything from the commandline.

---

