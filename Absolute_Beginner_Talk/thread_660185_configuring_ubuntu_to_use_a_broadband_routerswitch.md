---
title: "configuring ubuntu to use a broadband router/switch"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by cheetah_thompson on 2008-01-06
I'm new to Linux/Ubuntu as of yesterday and I am trying to figure out how to connect to my broadband router. It is a Zonet 802.11g ZSR1134WE wireless broadband router with 4 Ports LAN switch. It is connected to a Paradyne ADSL broadband modem. With the latter I have been successful in configuring the PPPOE settings and have a solid broadband connection. The problem with this is that I cannot then connect the wireless broadband router, so Windows XP laptops in the house cannot then use the wireless network. 

So I want to be able to connect with an ethernet cable to the broadband router/switch directly (since the Linux desktop sits next to the router anyway). How would I go configuring Ubuntu to detect this?  Do I need a driver for the Zonet router (I didn't find one for Linux, though it does say its compatible with any OS that understands TCP/IP)? Do I need to set a static IP address or can an ip address be autmatically assigned as under Windows? Please assume I know nothing other than how to modify files using 'sudo gedit filename' with the terminal and how to get to the 'Network Settings' GUI in Ubuntu.

Thanks in advance.

---

### Post by steveneddy on 2008-01-06
Just plug in and if the ethernet works in your laptop, it should connect if you have the router to DHCP and the lappie to get the IP automatically (DHCP).

There shouldn't be a problem. It should be automatic. My system just hooks up, no matter which computer is there, and there is internet.

If the other PC's in the house can access the wireless, then the router should assign an IP automatically and you can open a browser and get on the internet.

---

