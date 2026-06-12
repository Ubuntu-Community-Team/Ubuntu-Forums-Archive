---
title: "Change permissions"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by ronjan41 on 2007-06-04
Hi, another newbie!
I want to add a line to the etc/modprobe.d/alsa-base file but am refused as not having permission. I tried sudo su to get to root and entered what I thought was correct but it did not work. What do I need to type in Terminal to give me permission to change the file?
TIA
Ron

---

### Post by pbw on 2007-06-04
use sudo in front of whatever command you need to do as root.

ie. sudo vim /etc/modprobe.d/alsa-base (or whatever)

to switch to root in ubuntu to perform multiple terminal tasks enter, sudo -s

When using sudo, simply enter your user's password when you are prompted for one.

---

