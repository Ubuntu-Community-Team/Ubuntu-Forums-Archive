---
title: "Help with connecting an Ubuntu 7.04 to windows XP pc via LAN"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by mattesticels on 2007-04-07
hello all, 

this is my first post in these forums and i have just recently installed Ubuntu 7.04 and would like to connect my Ubuntu machine to Windows XP via a LAN cable for file sharing and internet access. i wont to do this because my windows XP pc is connected to a wireless network already and i would like to share that connection to my ubuntu pc.

I have no idea how get the netgear wireless dongle working on Ubuntu. so i thought i would try this way, maybe it is easy but i have no idea. 

the specs on my windows pc is as followed 
Netgear wireless USB adapter wg111

the wireless router i have is a Netgear wgr614 v6

so please if someone could help me i would be very thankful :)

---

### Post by siciliancasanova on 2007-04-08
Is Windows connecting to someone else's network?

If not and you are connecting to your own network, do you have a wireless card on your Ubuntu machine?

---

### Post by mattesticels on 2007-04-09
nah windows is connecting to my home network and i do not have any wireless card on my ubuntu machine just a wireless USB adapter on my windows PC, 

the two computers are connected by a lAN cable and i wont to know if i can set up connection between them so i can share my internet connection and network setting to the ubuntu machine through my windows PC if at all possible :confused:

---

### Post by siciliancasanova on 2007-04-09
Try to ping the router after you have configured your Windows machine after following [this page]("http://www.microsoft.com/windowsxp/using/networking/expert/crawford_02july01.mspx").

---

### Post by HereInOz on 2007-04-09
If you are connecting directly from the Ubuntu machine to the XP machine, you will need to use a cross-over ethernet cable.  It is a different wiring configuration than a standard ethernet cable.

Once you have that, you should be able to set up Internet Connection Sharing on the XP box and share the connection with the Ubuntu box.  You may have to set up a static IP, gateway and DNS server addresses on the Ubuntu box - sometimes Ubuntu does not pick up the DNS addresses from the DHCP server (your XP machine).

---

