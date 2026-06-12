---
title: "Forwarding ports"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Skull Kid on 2007-05-31
Hi, I am fairly new to Ubuntu and Linux itself; I'm having trouble forwarding ports for Deluge. From what I remember from Windows you had to set up a Static IP, by typing in ipconfig in the cmd prompt and entering appropriate information in a manual connection and then finally opening the ports in the router settings. I'm assuming it's similar in Ubuntu but I'm not sure where to find this info. I copied the IP from my router settings but apparently that one keeps changing. Also, on my network settings also shows up two wired connections (eth1, eth0) which is confusing me as well. I did manage to get Deluge working for a while with settings from the router setup, but like I said it doesn't last long as the IP changes constantly.

Thanks in advance for any help

---

### Post by Ocxic on 2007-05-31
your ip shouldn;t chage all tht often, if it is something wied is goin on,, check your router setting for: dhcp lease time abd extend it. if posible setup a statice ip between you and your router so it wont change.

eth1 & eth0 are both netwrok connects but only one should be active and have an ip if both do or they switch after you reboot, then you'll have to disable one, or unplug it from the network.

then just do as you did for windows.

---

### Post by irish_flu on 2007-05-31
What kind of router are you working with?  Most of them will let you assign a static IP to a workstation; if possible, this is what you want to do.

---

### Post by TheOtherShoe on 2007-05-31
For Ubuntu, instead of ipconfig use ifconfig. That will show you any IP address assigned to eth0 or eth1. It is usually the case that eth0 is the wired ethernet connection, and eth1 is the wifi connection; but if you have two ethernet connections, then eth1 might represent the second connection. On the other hand, sometimes parts of Ubuntu get a little confused about whether a network interface is ethernet or wifi. This could be one of those cases.

You can figure out which one you should look at by reading the output of ifconfig: hopefully only the connection you are actually using has been assigned an IP address - so if only one of them shows an IP address in ifconfig then go with that one.

Other than determining your IP address, I think that all of your configuration should be done on the router. Most routers have an option to always assign the same IP address to a certain computer. You can probably find this in the DHCP settings. Assign a permanent IP address to your computer, and then use that IP address in the port forwarding settings.

---

