---
title: "Configuring Wireless Network"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by justinesalo on 2005-11-29
I've googled and messed around for hours, but now I'm stuck.  I have the Windows driver--it shows up under System>Admin>Wireless Windows Drivers.  But when I hit the "Configure Network" button it takes me to my Network Settings where there is no wireless connection and no "Add" button.  I think I'm supposed to be adding something into my /etc/network file along the lines of:

iface wlan0 inet dhcp
wireless-mode managed
wireless-essid deansnet
wireless-key **************************

How do i find out my wireless-essid, mode and key or whatever else needs to go in this file?  Am I on the right track here?

---

### Post by kairu0 on 2005-11-29
Editing your /etc/network/interfaces file by hand is a sure way to get your network running. Even though it may be possible in the GUI, it'd be my choice to use the console like you are trying to do.

Are you using ndiswrapper? If so, do a "ndiswrapper -l" at the console to make sure your driver is there. Then, do a "ndiswrapper -m" to make sure the module is there. (You said that it shows up under Windows drivers but it's a good idea to double-check.)

Your essid, key etc. should be available by logging into your router from a web browser. Refer to the manual for your router for that part as every router is a little different.

---

### Post by Anomaly on 2005-11-29
I'm pretty new to Ubuntu also, but to install a windows driver for your card, you should use ndiswrapper which is a package that you can search and install using synaptic.  Instructions on using ndiswrapper can be found all over the net including these forums.

For the network essid, you should know it, you set it up when you configured your router. If not, it will probably be "default"

---

