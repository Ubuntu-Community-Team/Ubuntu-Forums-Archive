---
title: "LAN Connectivity problem"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by jcwurtenbaugh on 2007-06-04
I installed Efty and was so happy with it that I downloaded Feisty and wiped out the Windows partition. I am going to use the 3 year old Sony VAIO as a Linux work station.

HOWEVER, my plans have run into a major snag. The machine simply will not connect to a wireless network.  My home system is an ordinary Netgear router about 4 years old, running off a cable modem. It could not be more vanilla. With Efty, I ended up using Network (or Network tools, I forget which) to input the various IP addresses by hand. Once done, it connected with my LAN with no problem, simply requesting and receiving the password on the first connect  like my Windows machines. I actually installed 7.04 as an upgrade over 6.10, and it worked after that without any major issues. (The only reason I did the complete reinstall was to  erase the partition cleanly.)

Now, however, Network tools gives me only the 'Wired' options for Eth1 and Wlan1. On the toolbar, the basic  management tool  indicates Networking and wireless are enabled. But no matter what network I specify (I live in Mountain View, Ca, and Google WiFi is also available), the blankety-blank program indicates that it is unable to connect. I cannot input addresses either manually or by DHCP as there is no Wireless option presented in the Administrative tools menu. 

My best guess is that some script is missing, and it is pretty simple. Does anyone know what? 

Also, I am downloading Efty again as we speak, and am strongly tempted to install it over 7.04, do the connection, and then upgrade, now that I have the partitions the way I like. Does this make any sense? Will it work?

Thanks in advance for any suggestions to these embarrassingly simple questions.

---

### Post by daimaru on 2007-06-04
does your wireless card show up when you enter
```
iwconfig
```
in terminal?

---

### Post by kevdog on 2007-06-04
Can you give us some more details relating to your wireless card??  How were the drivers installed?? What does /etc/network/interfaces file look like?

---

### Post by jaspen.p on 2007-06-04
Maybe you guys can help me as well. I just installed feisty on a comp I bought from my company for $20 bucks since they were switching out. Anyway I bought a Geforce graphics card and a 256 memory upgrade and am hoping to use it as a media server for about $120. 

Anyway my question is this: I had the shared folders working and even hooked up a network  printer to print over the network from my xp laptop all using a linksys game adapter that I had laying around. However, I moved the computer to the room that  I had the modem and router in and plugged it straight into one of the Ethernet slots in the router circumventing the wireless game adapter and, low and behold, I now can't even see my shared folders or network printer. Anyway, I plugged back in the cable to the wireless game adapter and it worked again. What's the deal? I've played around with the shared folder settings and clicked the WINS server box and that let me see the folders but not browse them. Has anyone else had a similar problem or know of a fix? It seems silly to me to have to use a wireless adapter when the router is less then 6 inches away.

---

