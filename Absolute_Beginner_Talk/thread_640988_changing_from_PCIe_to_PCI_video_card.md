---
title: "changing from PCIe to PCI video card"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by AlienTechKilla on 2007-12-14
OK.... running into the issue with the Nvidia 7300 PCI-e that everyone else is having. Since the general consensus is that the "NEW" nvidia driver is causing the issue (and I've never experienced crashes before this card) so I'd like to switch back to my old Nvidia 6200 PCI which operates with different drivers. I disabled the "Restricted Drivers" and shut down figuring after I switched the cards the system would auto detect my newer card. Instead I received an error about my "XConfig". Since I've heard of this XConfig before, I figure it's something I can change though I have no idea how to. Can one of you Linux Nuts help this beginner. 

PS... Can I do this change through the "safe mode" since I can't get X to start.

---

### Post by AlienTechKilla on 2007-12-14
By the way this is the output of the "startx" command:

Fatal Server Error:
No screens found
XIO: Fatal IO Error 104 (connection reset by peer) on X server ":0.0" after 0 requests

Again.... I sure they're is an easy way to do this but I just don't want to screw this up.

---

### Post by AlienTechKilla on 2007-12-15
Found another forum and resolved the issue by running **sudo dpkg-reconfigure xserver-xorg** and I'm good to go..... thanks alien..... your welcome.

---

### Post by siciliancasanova on 2007-12-15
Out of all commands to remember, that one has saved my *** so many times.  It might be a wise thing to lodge it in your memory.

---

