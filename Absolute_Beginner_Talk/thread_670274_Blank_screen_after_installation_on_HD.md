---
title: "Blank screen after installation on HD"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by andershl on 2008-01-17
I was a mainframe nerd, but I'm a REAL novice to Linux environments:

I downloaded Xubuntu, burned the CD and started it on an old Fujitsu Siemens C-4310 laptop, that I intend to set up for Web access in our guest room. Everything looked fine, the wireless network card blinked, I cut get on Firefox. Great.

Then I installed on the HD. After power down startup is fine as to the first line mode part, but on full screen it just shows a blank/light gray screen. The wireless network card becomes active, so in fact everything still seems to be hunky-dory except I'm missing the desktop and any input possibilities.

Re-installed. Still same thing. Now stuck.:confused:

---

### Post by taurus on 2008-01-17
Maybe you need to reconfigure your X server again.

Press <Ctrl><Alt>F2 and log in with your username and password.  Then run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, press <Alt>F7 to get back to GUI login screen.  Then restart X with <Ctrl><Alt>Backspace.

Otherwise, you can also reconfigure your X server with

```
sudo dpkg-reconfigure xserver-xorg
```

---

