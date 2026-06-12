---
title: "Helping a friend set up his Internet Card"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-12-10
I have a friend who just installed Ubuntu this morning, he found out that his Internet Card isnt working and he has asked me to post in the Ubuntu forums for help. He has a built in Broadcom 802.11 WLAN Adapter, is their anyway for him to get it to work?

---

### Post by RobotoWorks on 2007-12-10
Bump....

---

### Post by ireneybean on 2007-12-10
if he has a regular (wired) NIC have him hook it up to do this.  Go to System->Administration->Restricted drivers manager and enable the firmware for the broadcom device.  It may give an error about not finding the package or something of that sort.  In that case he should go to system->administration->software sources and enable everything on the ubuntu sources tab and try again.

---

### Post by RobotoWorks on 2007-12-10
Thanx, what should he do if he doesnt have the Wired NIC?

---

### Post by ireneybean on 2007-12-10
go here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)
scroll down to Offline Install (and in fact the internet enabled install in the section above it contains a much more detailed explanation of what I posted earlier)

---

