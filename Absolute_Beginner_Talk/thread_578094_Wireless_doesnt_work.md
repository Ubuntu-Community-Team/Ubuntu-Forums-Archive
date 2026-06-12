---
title: "Wireless doesnt work"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by NurChiN on 2007-10-16
How to install wireless in Insiporn 1520

---

### Post by drascus on 2007-10-16
Try this list:

[http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

Also you may want to post the result of running the command: lspci in the terminal in this thread if you don't find your answer there. That way people know what type of hardware you are running.

---

### Post by xrshalar on 2007-10-16
So, you have a dell laptop with Intel processor.

I'm using Feisty on an HP Omni Xe3 notebook.
I have been plinking with wireless myself lately.

I tried several pcmcia cards and have been most happy with a Netgear...  it is and old card, MA401. 

Linksys WPC55Ag was a no go for me.

I simply leave the wireless in roaming mode and when I am in range of an access point, just left click on the "network" icon and select the wireless network that I wish to connect to.  If it's open, I'm in.  If not, well I'm out.

Not sure what the embedded wireless is on your Dell, but you should find out.

---

### Post by strabes on 2007-10-17
Drascus already said this but I'll clear it up a bit. Please run this command in a terminal (Applications > Accessories > Terminal) and paste the output in this thread. ```
lspci
```

This command basically outputs a list of all of your major hardware. We need to know what kind of wireless card you have so that we can tell you the appropriate method to get it working.

---

