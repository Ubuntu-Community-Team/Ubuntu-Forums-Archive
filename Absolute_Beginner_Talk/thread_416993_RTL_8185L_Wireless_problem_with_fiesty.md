---
title: "RTL 8185L Wireless problem with fiesty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by jvcd666 on 2007-04-21
Hi 
I am having problems with a realtek chipset RTL 8185 with fiest. After checking on the supported chipset list it appears to work out of the box with previous versions of ubuntu so I'm assuming it works with the newest, however I cant get the @~$%:@ thing to work :(  I have tried both ndiswrapper and the graphical version ndisgtk but both give me the same error

 sh: Syntax Error "(" unexpected ( expecting "}")
module configuration already contains alais directive

I have no idea what this means.  

lspci output
01:0a.0 Ethernet controller:Realtek Semiconductor co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (REV 20)
lspci -n
01:0a.o  0200:  10ec:8185

Any help and suggestions would be very welcome. 

ps

Words of 1 syllable or less appreciated :)

---

### Post by Icemanyurt on 2007-04-21
I am having the same problem, here is one solution (or so they say)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)

I am using this: 02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

I don't even see wireless connection under network tools...If I find anymore, I will share it, but right now I don't have anything...

---

### Post by jvcd666 on 2007-04-22
Thanks for that. found the blacklist under /etc/modprobe.d/blacklist and commented out the entry for rtl818x. I now have an entry for my wireless card under networks and it can detect my essid. however it shows a signal quality of 0 even with my lap top almost on top of the router. any other ideas would be appreciated

many thanks

---

### Post by Pobega on 2007-04-22
Does it should signals above 0 for other wireless routers in the area? I doubt you're the only one, so try running "iwlist eth* scan" (Substituting * with the number of your interface) to see the quality of everyone's network.

---

### Post by jvcd666 on 2007-04-22
Tried scaning for other networks found one more it also showed signal strength of 0.

---

### Post by euchrid on 2007-05-24
I also have an RTL 8185, and got it to work by commenting out the line referring to 'rtl818x' in /etc/modprobe.d/blacklist, then rebooting (this allowed Network Manager to find the card); then, in Network Manager, I added an 'x' to the ESSID, and it worked! Bizarre, but at least I can get back on the internet and network.

---

