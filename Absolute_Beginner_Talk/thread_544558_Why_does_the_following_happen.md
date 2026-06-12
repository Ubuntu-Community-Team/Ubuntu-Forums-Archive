---
title: "Why does the following happen?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-09-06
1. I need to press on the shutdown/reboot button twice before it actually reboots or shuts down.

2. I have to restart my computer to get a decent Wifi signal? With this I might be working on my laptop for hours until the signal goes really bad. A reboot then pushes the signal back to full strength.

Anyone willing to help, much appreciated.

---

### Post by asmoore82 on 2007-09-06
> **Bagboy23 said:**
> 1. I need to press on the shutdown/reboot button twice before it actually reboots or shuts down.
On most computers I've seen, pressing the button causes a dialog to pop up asking you
what you want to do -> logout/lockscree/switchuser/suspend/hibernate/restart/shutdown
?maybe you just aren't waiting for the dialog?

> **Bagboy23 said:**
> 
2. I have to restart my computer to get a decent Wifi signal? With this I might be working on my laptop for hours until the signal goes really bad. A reboot then pushes the signal back to full strength.

I'm not sure about the signal problem but my laptop does the same
when I wander out of range and come back.
A much better way to get it back to norm is to just restart the networking instead of the whole computer;
to do this open a terminal and ...
```
~$ sudo /etc/init.d/networking restart
```

---

