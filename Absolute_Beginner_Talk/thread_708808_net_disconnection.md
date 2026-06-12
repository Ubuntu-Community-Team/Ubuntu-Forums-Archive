---
title: "net disconnection"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-26
net is often getting disconnected in ubuntu 7.10 but works fine under windows.it was working fine some days back.

---

### Post by Crafty Kisses on 2008-02-26
> **adi_das said:**
> net is often getting disconnected in ubuntu 7.10 but works fine under windows.it was working fine some days back.

Are you on a Wired connection or Wireless?

---

### Post by adi_das on 2008-02-27
wired usb

---

### Post by bumanie on 2008-02-27
Suspect you have the ipv6 connection problem. Try this 
> sudo gedit /etc/modprobe.d/blacklist
Scroll down to the bottom of the gedit list and type
blacklist ipv6
Save and reboot. 
If ipv6 is the problem, this will fix it. If not you can reopen the gedit list as per initial command and then delete what was added. Save and reboot and your computer will be back to how it is now.

---

