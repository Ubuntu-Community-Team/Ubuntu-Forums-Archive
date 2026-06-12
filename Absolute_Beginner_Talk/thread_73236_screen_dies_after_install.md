---
title: "screen dies after install"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by dataddict on 2005-10-08
Hi, I'm new to Ubuntu and linux, but decided to try anyway.. Installation worked well (after finding out to give noapic as a parameter at install). 

I'm installing on an acer travelmate 3210 wxmi.

When installation ended and the system rebooted, Im presented with a nice Ubuntu logo and some logging text. 
After this the screen just dies, and no input helps. not even a blind login attempt.. PLZ help this newbie!

---

### Post by TheWheat on 2006-11-29
1. Get the console (Ctrl+alt+F1)
2. Login
3. Set up your network connection
4. Type "sudo apt-get install xorg-driver-fglrx" to install the fglrx driver
5. Type "nano /etc/X11/xorg.conf" and under the "Device" Section modify 'Driver' to be "fglrx"
6. Save the file (Ctrl + O) and Exit (Ctrl+ X)
7. Type "startx" and hopefully it should work

---

