---
title: "Wireless connection - strange behaviour"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by RogerD on 2007-03-14
Hi

Installed ubuntu on my new PC yesterday - it took all of 15 minutes. Unfortunately, it's been heavy going since that initial success.

My current big problem is with my wireless connection. I've an Edimax USB wireless adapter, supplied by those helpful people at the Linux Emporium. This comes with a CD containing the necessary drivers. I installed the drivers successfully, and soon had a wireless connection with Firefox working just fine.

Here's my problem: when I now switch on my PC, the network connection icon on my panel indicates that I have no wireless signal. I go to System>Administration>Networking, and the Networking settings window appears. I'm told "Wireless connection The interaction rausb0 is active", "Ethernet connection not active", and "Modem connection not configure". The Default gateway device box is empty.

If I click on the wireless connection, and then click on "properties", the properties window opens - with all the relevant fiedls, EISS, WEP, completed - and almost immediately, without me clicking anything,  the signal strength bar on the panel icon goes green, indicating 100% signal strength. I go back to the Network setting window, and set rausb0 in  the gateway device box, and click OK.

Here's the really strange bit: now, sometimes Firefox works, but generally I get a "server not found message", and, if I restart my computer, I'm back to square one, with zero signal strength and an empty default gateway device box. I suspect that if I could keep this box filled, all might be well.

All suggestions much appreciated. Maybe it's possible to set this box from the command line.

Roger D

---

### Post by RogerD on 2007-03-14
Hi

I've solved this problem. I deactivated then reactived the wireless connection, which got me a permanent entry in the default gateway device box, and all now seems fine.

A variation of 'if in doubt re-boot approach'..


Roger D

---

### Post by RogerD on 2007-03-14
Oh dear, spoke too soon. I have to go through the deactive-reactivate routine everytime I switch my PC on. Someting still not right.

Has nobody had this problem before?

Roger D

---

