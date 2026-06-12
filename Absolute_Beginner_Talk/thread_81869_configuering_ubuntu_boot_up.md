---
title: "configuering ubuntu boot up"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by grathis on 2005-10-25
How do I configuere ubuntu to not spend 5 minutes looking for a network , and 2 minutes looking for a time server while booting up? 

It is kind of embarrassing.

---

### Post by Xian on 2005-10-26
Try removing the ntpdate application for the time sync issue.
Probably something similar for the network....

---

### Post by davmac on 2005-10-26
Not very elegant but you can press Ctrl-C. There are other threads that suggest you can move it down the order of the bootup processes, but somebody mentions that this causes their DHCP to stop working. If you search the forums for "configuring network timeout" you'll find the relevant threads on this.

One person suggests reducing the timeout to something more suitable for yourself. To do this, open up a terminal and type "sudo gedit /etc/dhcp3/dhclient.com" and where you see "#timeout 60;" replace it with "timeout 5;" or whatever value you feel appropriate.

HTH,

Dave Mac

---

