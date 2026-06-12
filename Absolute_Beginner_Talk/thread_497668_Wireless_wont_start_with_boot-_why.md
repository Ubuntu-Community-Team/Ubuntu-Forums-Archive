---
title: "Wireless wont start with boot- why?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by fireflyfx on 2007-07-10
Hi- using xubuntu 7.04- why wont wifi work automatically after booting up?
Everytime i have to go into applications>system>network and untick then retick the box next to "wireless connection" in order to get it to work. Then it works perfectly until next boot. Here is my /etc/network/interfaces file:

auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless-mode managed
wireless-essid
wireless-key1 s:
wireless-key s:



auto eth0

(blanked out ssid and keys) PLZ HELP- its driving me nuts.:confused:

---

### Post by ev5unleash1 on 2007-07-10
This happens to me at times, make sure all settings are correctly and it's not doing any sort of hang on start up (this could be a drive issue which mostly happens on Restricted Wireless Drivers like some Intels). If not then if you don't mind try reinstalling Ubuntu (this solves most cases).

---

### Post by ugm6hr on 2007-07-11
Don't want to risk your connection (given it is working) - but worth trying Wicd if the built-in network manager is being annoying. It simplifies the whole process, and autostarts with each restart, and also adds WPA support.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Just download, double-click to install, add "/opt/wicd/tray.py" to a new entry in Autostarted Applications (Applications->Settings), then restart and it is obvious what to do from there.

---

