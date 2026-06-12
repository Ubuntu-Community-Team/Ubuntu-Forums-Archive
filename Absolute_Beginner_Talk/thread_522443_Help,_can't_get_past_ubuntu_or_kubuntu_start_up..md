---
title: "Help, can't get past ubuntu or kubuntu start up."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Jonnothin on 2007-08-10
I have Ubuntu and Kubuntu on my system for dual booting but when I try to start up either one it gets just past the loading bar and immediately goes to a silver screen with horizontal black lines while the silver-ish liquid moves.

I do believe it is my graphics card because to start the live CD of either OS I had to press F4 and change the resolution to 800 x 600 32b and press F6 as well and type in noapci to get it to start either live CD.

How do I change the screen resolution of a OS already on your system? Is it even possible? If not what else can I do?

---

### Post by everythingsused on 2007-08-10
I've never seen that problem before, so I can't tell you if it is a resolution problem. But if you want to try that, you can change your screen resolution in your xorg.conf file. Boot the OS into safe non-graphical mode, login then run ```
sudo emacs /etc/X11/xorg.conf
```. Replace whatever resolution is listed with "800x600."

---

### Post by splintercellguy on 2007-08-10
My suggestion is to do sudo dpkg-reconfigure xserver-xorg in recovery mode and reboot. Make sure to backup /etc/X11/xorg.conf before starting.

---

