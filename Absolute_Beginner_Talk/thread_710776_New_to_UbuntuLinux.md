---
title: "New to Ubuntu/Linux"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by 17ezeerb on 2008-02-28
I'm just now finishing up installing Ubuntu and I have one question for the moment.  I need to install a Linksys wireless card.  Can I install using the driver disk it came with? :confused:  I can hardwire if I have to but I'd rather not.  I'm sure I'll have more questions once I get past this.  Thanks for any help and suggestion.

---

### Post by overdrank on 2008-02-28
> **17ezeerb said:**
> I'm just now finishing up installing Ubuntu and I have one question for the moment.  I need to install a Linksys wireless card.  Can I install using the driver disk it came with? :confused:  I can hardwire if I have to but I'd rather not.  I'm sure I'll have more questions once I get past this.  Thanks for any help and suggestion.

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by 17ezeerb on 2008-02-28
Hi Overdrank,  Man, that was the fastest reply to a question on a forum I've ever had.  I think this card is a dud and I'm going to have to take it back and exchange it. :(  Too late for tonight, I'll have to get back to you tomorrow.  This is par for the course for me. :)  Thanks for trying to help.  Hope you can help me tomorrow.

---

### Post by SunnyRabbiera on 2008-02-28
well first why are you using such an old version (according to your profile you are using a non supported version of ubuntu)
also second some wireless things might not work on ubuntu, this is of no fault of ubuntu or linux but more fault of the manufacturer who mainly focus on windows

---

### Post by tad1073 on 2008-02-28
[Lynksys Compatibility/madwifi](http://madwifi.org/wiki/Compatibility/Linksys)
[Supported cards](http://madwifi.org/wiki/Compatibility)

---

### Post by bmobley on 2008-02-28
hate to hijack and/or butt in but i have the same issue.  am using 7.10 and no wireless.
 

01:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

thanks

---

### Post by dark_harmonics on 2008-02-28
I have gotten any wireless card ive come across to work through the following methods:

1. Use the most current release which has the latest kernel. Most cards are supported natively so just plug and see if it plays!

2. Madwifi supports quite a few wireless cards. The supported list posted above should help

3. ndiswrapper can be used to attach windows based drivers to the  ndiswrapper module that linux can see:

sudo apt-get install ndiswrapper

sudo ndiswrapper -i (whateverdrivernameis).ini
sudo modprobe ndiswrapper

When using ndiswrapper you should add it to your /etc/modules so that it starts it with each reboot.

---

