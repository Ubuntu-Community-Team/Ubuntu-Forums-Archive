---
title: "Good internet connection but no network connection??"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-17
I have three comps here (Gateway with XP, Compaq with Ubuntu 6.06.1, and Toshiba laptop with dual boot Ubuntu and XP). I have good internet connection via ethernet cable (all three) running to router, which is plugged to satellite modem. The laptop shows wired network connection in NM icon and can ping the Compaq just fine, and ping the router just fine, but not the Windows box. The Compaq shows no network connection, but can ping the laptop fine, and the router, but not the Windows box. I have them all in the same workgroup, with static ip and all other settings match on the laptop and the Compaq. Just can't figure out why I have no network connection on the Comnpaq, or why I can't ping the Windows box from either of the other two comps. I know this is kinda long winded but I have been at this for the past three days and getting really frustrated. Any help would be greatly appreciated. Thanks in advance.

---

### Post by irish_flu on 2007-01-17
Are you running any firewall software on the Windows box that might be ignoring ping requests?
[
As for the "no network connection" on the Compaq, I'm confused; if you can ping stuff, it sounds like there's a connection.  Is anything on that machine not working (besides not being able to see the Windows box)?

---

### Post by jerrynewt on 2007-01-17
Everything seems to be working on the Compaq, and it was the firewall on the Windows comp stopping the ping request. I can now ping all comps and router from all comps but still show no network connection in NM icon on both linux comps. I ran ifconfig on both and made sure I had the right ip addresses and mac addresses right. I have static ip's for both linux boxes--should I change that to DHCP instead?? It probably has nothing to do with anything, but the compaq uses eth1 for internet connection (ethernet cable) and the laptop used eth0 for connection. Do I need to change either one of those?

---

### Post by Shatrat on 2007-01-17
The offending desktops which show that they are disconnected sound like maybe they are just monitoring the wrong network device.  Right click the network manager and go to properties and make sure that it is monitoring the device you actually have connected to the router.

---

### Post by jerrynewt on 2007-01-17
OK I'll give it a try-- thanks!!

---

### Post by jerrynewt on 2007-01-17
When I bring up NM there is a header at the top saying Location. What is supposed to be in this box--the Ip address of the computer, or Domain name or comp name?  Everytime I try to enter a location such as the computer name I get a info box saying it is changing the profile, and still no network connection.

---

### Post by jerrynewt on 2007-01-17
Well I didn't put anything in the Location box and put all comps on DHCP. I now have network connection on Laptop (with two icons in tray-one says "wired network connection",when I hover the mouse pointer over it, and the other says Network connection: eth 0) Still don't have network connection on Compaq or windowz box, but all three have internet connections. This is about to get the best of me, I have tried everything I can think of. Anyone out there that can walk a shiny newb through this--WAN,LAN,WLAN--it's giveing me a headache. All suggestions will be greatly appreciated. Thanks!

---

