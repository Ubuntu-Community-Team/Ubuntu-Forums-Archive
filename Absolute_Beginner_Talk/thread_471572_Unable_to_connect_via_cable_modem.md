---
title: "Unable to connect via cable modem"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by NCAANFI on 2007-06-12
Hi I've just completed a clean install on a PC I just built

Specs
CPU: AMD X2 3600+
Mobo: Asus M2n8 vmx
Video: ECS 256 nvdia 7300gt
Wireless card: Asus WL138G
LG SATA Dual layer burner
WD SATA 250gig HDD
Ram 1 gig

ISP: Optusnet Australia
Wireless Router: WRT54gl
Cable Modem: Motorola SB5100

But now I can't connect to the internet, I've plugged into the ethernet adapter cable modem -> PC direct, I've removed the router, Ubuntu picks it up and says I'm connected but all connections time out. I've tried a manual config using what's on the Win XP Pc but still no go. I've tried DHCP and still no good.  Eventually once I can get the ndiswrapper and stuff this will become a wireless connection until then I'm chained to the basement. 

I also had this issue on install and am not too sure if its related.

I boot up using the burned ISO CD. I get to the menu asking me what I'd like to do. I select option 1 but the following errors come up

18.239616 MP-Bios bug 8234 timer not connected to io apic
18.418467 Kernel Panc - not syncing 10 apic +timer doesn't work boot wth apic = debugand send report.

I did the f6 noapic thing which let me install.

Thanks for any help or suggestions.

So far everything works fine, but until I can get the necessary codecs etc to play as this was supposed to be a media centre PC. If you need more nfo please let me know. (also how to get that info if I have to do the command line stuff)

---

### Post by bscbrit on 2007-06-12
It sounds like it might be a DNS problem. For example, if you can ping 82.211.81.186 but not 'ubuntuforums.org' then the problem is almost certainly your local DNS settings.  What is the content of '/etc/resolv.conf'?  In fact, to help, what is the content of '/etc/network/interfaces' as well?

---

