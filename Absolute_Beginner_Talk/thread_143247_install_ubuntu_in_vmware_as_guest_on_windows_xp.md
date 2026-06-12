---
title: "install ubuntu in vmware as guest on windows xp"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by al_gomez on 2006-03-12
Hello, I recently installed ubuntu 5.10 on vmware server (beta).  The host is a laptop toshiba satellite m35x-s149. Running windows xp pro sp2. 
The problem I have is that I can't get internet connection. I used a community wireless network provided by my landlord. 
I don't know why ubuntu can't recognize the wireless. 
VMware has this settings:

Memory 192 MB
Hard Disk (IDE 0:0) 
CD-ROM (IDE 1:0)     Auto Detect
Ethernet                  NAT
Processors               1

when I open the Virtual Network Editor, I am no surre what setting I need to have. 
Under summary I see:

VMnet0 (bridged)  Bridged to Atheros AR5004G Wireless Network Adapter - Packet Scheduler Miniport

VMnet1 (host-only) a private network shared with the host
VMnet8 (NAT) Used to share the host's IP address

There are more tabas, I am not sure if is neccesary I post what they show. I would like to ask if someone can help me with the VMWare settings, and what other stepes after installation of ubuntu on the virtual server s done, I need to do. 

Any help is greatly appreciated. 

Thank you. 

al

---

### Post by Klejs on 2006-03-12
Ubuntu dont see the card you have because it will use an software emulated card, but if you use birdged it should work, that worked fine for me anyhow...

---

