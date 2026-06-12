---
title: "almost that same internet problem dapper people have been having"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by darckhart on 2006-06-03
ok i was previously using breezy, but just bought a new hard drive a week ago, so decided to install dapper on it. (did not check to see if the internet was working during the livecd session.) currently, the internet does not work and i need a little bit of help figuring out where to go from here. (btw, yes, internet works with breezy and winxp.)

i use a wired lan connection and i specify all my settings (e.g. no dhcp). my provider is sbc dsl.

eth0: 192.168.1.149
gateway: 192.168.1.1

1. i can ping the router. (e.g. ping 192.168.1.1)
2. i can ping wan ip adresses. (e.g. ping 207.46.19.60)
3. i cannot ping the name url. (e.g. ping [www.microsoft.com](www.microsoft.com)) it just sits there. forever.
4. in /etc/resolv.conf, i have listed sbc's dns servers for my locale only; my router ip is NOT included. (avail from [http://dedicated.pacbell.net/faq/FAQs_techsupport.html#servresolv](http://dedicated.pacbell.net/faq/FAQs_techsupport.html#servresolv))

the fact that i can reach the ip but not the name suggested that it would be a dns problem, but apparently dapper is doing something weird?

i have also:
1. rebooted/power-cycled the router and the dsl modem.
2. disabled ipv6 system-wide as well as in firefox

what can i do from here? thanks for advice.

---

### Post by Dr. Nick on 2006-06-03
sounds like dns to me, can you log into your router in a web browser? 

It may be worth a shot to confiigure linux to obtain an ip from the router and not to specify one right now. Once you are sure linux is getting an ip you could specify it then, Did you use command line or a gui to set up static ip's?

---

### Post by darckhart on 2006-06-03
i just tried dhcp (system, network, switch to dhcp) and that doesnt work either. =(

---

### Post by Dr. Nick on 2006-06-03
hmm, not sure if this will do it but worth a shot
type these into a terminal they will disable - enable - then try and get a ip

sudo ifdown eth0
sudo ifup eth0
sudo dhclient eth0

---

### Post by darckhart on 2006-06-04
hm i'm pretty sure it's a dns problem, but everything i've done *should* have worked.

tho, i tried running "dig . ns @203.13.28.12" and it tells me that no servers could be reached... wth?

---

### Post by uzi09 on 2006-06-04
as stupid as this sounds....

have you double checked your DNS servers to ensure they are the correct ones? might wanna double check with your ISP too.

---

### Post by darckhart on 2006-06-04
yea i'm fairly certain they are since i'm able to connect via this winxp box which is configured the same way. grrrr dapper

---

### Post by uzi09 on 2006-06-04
hmm :\

that is odd. try going to this address from your browser:
72.14.203.99
(google.com)

also, one other thing you could try is to plug it directly to the internet and check to see whether it is dapper causing the problem or your router (with dapper).

---

### Post by darckhart on 2006-06-05
yep did those too. it's definitely something about dapper. back to searching these forums.

---

### Post by togume on 2006-06-05
I'm glad I found this and someone else is having the same issue I am. I have an HP dv1000 laptop (for documentation's sake) with an intel 2200 internal card. I can ping AND even use nslookup successfully, but when I open firefox it goes nowhere. It is set up with DHCP through either wifi-radar or network-manager with the same results. Right now I am using the XPPro partition which is also set up to use DHCP with no problems. As a sidenote, I am sitting behind a realtek DSL gateway and a linksys wireless router and have manually tried to edit the NDS...

---

### Post by darckhart on 2006-06-05
hm some specs in case anyone needs to know:

mobo: Asus A7V266E, VIA KT266A chipset (onboard ethernet controller DISABLED)
nic: D-Link RTL8139 (rev10)
router: Linksys WRT54g w/HyperWRT Thibor firmware
modem: SBC Efficient Networks Speedstream 5100

if in winxp i would reinstall the drivers for the card next, but i'm not sure how to do that in dapper.

also, dunno if it's relevant, but after googling, seems the internet issues have cropped up after kernel 2.6.21. can anyone verify this? my old default clean breezy install detected all the hardware fine and everything worked from the get go. i believe i used kernels 2.6.8, 2.6.10, and 2.6.12 in breezy.

oh and internet did NOT work with the livecd session as well.

perhaps i will cross post this in the support/networking forum also.

---

### Post by togume on 2006-06-06
Update:

I was not able to change the DNS servers by going to the gui so I changed the the resolv.conf directly to be the same as the outgoing router/gateway instead of 192.168.0.1 as primary and xxx.xxx.xxx.xxx as secondary. This fixed the problem. 

This leads me to believe it is something weird with the handling of internal DNS servers.

---

### Post by invisage01 on 2006-06-06
same problem here with the D-Link router... 

not sure if it is a d-link problem or a Dapper problem.. but it is damn frustrating!!!

Using DHCP in XP works.. DHCP in dapper doesn't ... but when i stuff around and store my DNS server IP address (and this is a mission in itself sometimes) it will finally work..

but then wipe my DNS settings on reboot?

what the?

---

### Post by darckhart on 2006-06-11
turns out my prob was actually because of the winxp box. one day, i happened to have the winxp box off, and ta-da! dapper could access the dns servers just fine. weeeeiird.

---

### Post by Saxphile on 2006-06-11
For people having this problem and using DHCP to get an IP address, see this solution:

[http://www.ubuntuforums.org/showthread.php?t=187466&highlight=dhclient.conf](http://www.ubuntuforums.org/showthread.php?t=187466&highlight=dhclient.conf)

For people on static IP - I don't know. I'm still working this out myself.

---

