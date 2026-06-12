---
title: "[SOLVED] Virtual Box IP settings"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by mynogan on 2007-12-24
Following the advice offered in [http://ubuntuforums.org/showthread.php?t=645476](http://ubuntuforums.org/showthread.php?t=645476), I decided to install Ubuntu 7.10 in Virtual Box. It looked promising, there's isn't a need to mess with the graphics, mouse, and sound settings. And it seems to use less of the host PC resources. But I encountered a problem with the network settings. Virtual Box/Ubuntu created a new network with the 10.0.2.x range (specifically, 10.0.2.15). The host pc uses, as with all my other windows and mac machines, the 192.168.2.x range. They are all connected to the router which is set at 192.168.2.1.  How do I set the Ubuntu virtual machine to the 192.168.2.x range. When I tried to manually set a static IP (e.g. 192.168.2.111), I could not connect to the Internet at all. What gives? :confused:

---

### Post by tomcheng76 on 2007-12-24
You need to set Virtualbox Network setting to bridge mode
[Manual]("http://www.virtualbox.org/download/UserManual.pdf")
search Host Interface Networking and bridging on Windows hosts

---

### Post by mynogan on 2007-12-24
Never mind. I solved the problem. Solution if anyone ever encounters this problem is found here:  [http://forums.virtualbox.org/viewtopic.php?t=1787](http://forums.virtualbox.org/viewtopic.php?t=1787)

---

### Post by mynogan on 2007-12-24
Thanks, Tom!

---

