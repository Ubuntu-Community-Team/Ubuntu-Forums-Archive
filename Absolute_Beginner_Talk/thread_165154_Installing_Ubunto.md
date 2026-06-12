---
title: "Installing Ubunto"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Rhyu on 2006-04-24
I have installed Ubuntu on an IBM P2 (233) laptop as the principle OS.  After completing the installation the system asked for my username and password.  I supplied this and instead of the desktop appearing a line appeared:
sampson/ubuntu/ $
The system is obvioulsy after a command, but what?

This is my first attempt at Linux (Microsoft man-but converted)  Can any one help me?

Rhyu

---

### Post by mips on 2006-04-24
Seems you have a problem with the X-server.

The file that holds the configuration:
**/etc/X11/xorg.conf**

The utility/command to reconfigure X:
**sudo dpkg-reconfigure xserver-xorg**

Problem solving wiki:
[https://wiki.ubuntu.com/DebuggingXAutoconfiguration](https://wiki.ubuntu.com/DebuggingXAutoconfiguration)

---

### Post by nalmeth on 2006-04-24
did you pick "server install"?
If so, it would have excluded the ubuntu-desktop and left you only with a base install.
in that command line, type:
sudo apt-get install ubuntu-desktop

---

### Post by skinnygmg on 2006-04-24
what's ***Ubunto***?

sorry... i had to

---

### Post by Rhyu on 2006-04-25
Thanks everyone for your help and also for the spelling lesson. Nalmeth gave me the clue and I re installed not as server and all is working fine.


Rhyu

---

### Post by nalmeth on 2006-04-25
Great news
welcome to the ubuntu world
have fun rockin in the free world

---

