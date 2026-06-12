---
title: "Please help me decipher my wireless problem"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Borgus on 2006-10-02
Hello all. I am a newbie to linux. I installed ubuntu (latest version, by burned disk) today at 9 AM and have been grappling with setting up my wireless network ever since. This situation is quite aggrevating. 

1) Why is it that under system>administration>networking>wireless connection properties there is no place to inter a WAP password. My network is WAP, not WEP. I am confused on what to do in this situation.

2) I tried installing two drivers (bcmwl5, bcmwl5a), but ndiswrapper -l reveals that both of these drivers are installed but invalid. I go to uninstall these drivers and it tells me that they are not installed :-k What is going on here?

3) I type in ipconfig into the terminal and i get the response "command no found." How could that be?

4) After installing ndiswrapper, the installation tools tells me I have the drivers installed but the hardware is not found?


So, what do you guys suspect the problem could be? Please help, I am desparate and frustrated ](*,)

[Edit: I am behind a d-link router, trying to install on a laptop that has a Broadcom card BCM4306 PCIID 14e4:4320]

---

### Post by Skia_42 on 2006-10-02
You can check if your card is a card known to work with Ubuntu [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

There is also a good trouble shooting guide [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").

---

### Post by Borgus on 2006-10-02
Thanks for the links. Could you please decypher what all those No's mean for my card? I'm still trying to learn this stuff and its late. Thank you very much for your effort.

---

### Post by Arevos on 2006-10-03
> **Borgus said:**
> 2) I tried installing two drivers (bcmwl5, bcmwl5a), but ndiswrapper -l reveals that both of these drivers are installed but invalid. I go to uninstall these drivers and it tells me that they are not installed :-k What is going on here?
There is a compatability list for ndiswrapper [here](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page). You could also try installing the latest version of ndiswrapper from source (that's a little more complicated though).

> **Borgus said:**
> 3) I type in ipconfig into the terminal and i get the response "command no found." How could that be?
ipconfig is a command that needs to be executed with administrator priviledges. Try typing "sudo ipconfig".

[QUOTE=]4) After installing ndiswrapper, the installation tools tells me I have the drivers installed but the hardware is not found?[/QUOTE]
Try looking through the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Borgus on 2006-10-03
OK. I might be getting somewhere (finally).

It now seems that I have working drivers. I can verify this by using the command "ndiswrapper -l" which reveals both a driver and hardware is present.

However, I do not think my wireless card is engaging. I try to turn on the hardware by using Fn+2 (default wireless powerup), but no dice. I even tried "sudo modprobe ndiswrapper", but still the LED refeuses to light up as if the hardware isnt even activated.

I also appears that when I do "iwconfig" that eth1 is my wireless, I know this isnt right and it should be wif0 or wif1. What can I do about these issues?

Also, once I figure out how to activate my wifi card, I will be trying to logon to a WPA network. 

Someone please end my frustration. I have put aside way too much real work (homework) trying to get this damn thing running ](*,)

---

