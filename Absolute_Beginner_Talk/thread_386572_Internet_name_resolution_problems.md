---
title: "Internet name resolution problems"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by earhornjones on 2007-03-17
Hello, all.

Please forgive my wanton ignorance.:confused: 

I am an absolute Ubuntu newbie, having installed it for the first time last night.

The installation went very smoothly, and everything seems to be working quite well, with the exception of my Internet browsing.  I am unable to browse the Internet by domain name.  

For example, if I enter "www.google.com" into the Firefox address bar, the browser times out.  However, if I use the ping utility to ping "www.google.com" I get replies, and if I enter the IP address taken from that ping into Firefox, it will open Google without difficulty.

The computer is on my home network.  It has a wired connection to a DSL router which is serving as a DHCP.  The same problem occurs whether I manually assign IP settings, or let the DHCP dish out the settings.  

Other computers on my network have no problem browsing the Internet.

I can access network shares and printers on other computers flawlessly. 

Any help would be greatly appreciated!

Thanks!

---

### Post by arvevans on 2007-03-17
**System/Administration/Networking/Wired Connection/DNS** will allow you to set the address of DNS servers for your system.

If you are using your WiFi Hub/Router as a DHCP server, it is possible that it does not have a pair of DNS servers configured in it, and thus cannot provide DNS services to your Ubuntu system.

Arv
_._

---

### Post by earhornjones on 2007-03-17
Aha!  I was overlooking that DNS tab.  Once it was pointed out, I found that my DSL Router was passing its own IP as DNS Server, which apparently is working for my other machines.  I manually configured the DNS on my Ubuntu box, and now I'm surfing happily.

Many thanks, Arv!

---

### Post by seano2101 on 2007-03-18
i am having a simular prob. except my computer keeps forgetting the DNS.  I tried it saving it as well but it after about 15  mins or so I have to re-enter it or change back to that locaction (home).

---

