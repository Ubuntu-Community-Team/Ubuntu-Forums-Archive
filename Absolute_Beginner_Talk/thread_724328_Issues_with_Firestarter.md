---
title: "Issues with Firestarter"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by caffienefree on 2008-03-14
Hi all,

Firestarter used to work fine for me, at some point it stopped, not really sure when. This is on Gutsy Gibbon 7.10.

When I open the application, I'm told: 

> Failed to start the Firewall
The device eth1 is not ready
Please check your network device settings and make sure your internet connection is active.

The firewall at this point is disabled. Clicking start firewall results in the same message.

However, there is no eth1 on my system. Under network on my screen, there are entries for eth0 (ethernet) and wlan0 (wireless). Under Preferences> Network Settings, I've set the Internet Connected network device as eth0 and the local connected network device as eth0.

ifconfig only has entries for eth0, lo, and wlan0. ifconfig eth1 results in eth1: error fetching interface information: Device not found. 

Does anyone have any suggestions or ideas regarding this situation?

---

### Post by Mauler5858 on 2008-03-14
Make sure that internet connection sharing is not enabled under firestarter's configuration.  If so it might be looking for the second adapter to share it to.

---

### Post by caffienefree on 2008-03-15
Thank you for your reply. No, Internet connection sharing is disabled.

---

### Post by oliviacond on 2008-03-15
you need disable eth1

edit your /etc/network/interfaces file and comment out the eth1 section , use # at the begining of the line to comment it out. use "gksudo gedit /etc/netwok/interfaces" command to edit the file

---

### Post by sayakb on 2008-03-15
Open firestarter GUI, goto Firewall->Run Wizard, and press forward.. there in the menu list, select eth0 or your network device you are actually using.. complete the remaining steps, done..

---

