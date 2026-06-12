---
title: "Having network problems, loosing hair"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Phatie Mcgee on 2006-07-12
hey guys.. im almost bald here and this network setup isn't helping ;) 

So here is what I have..
```

Cable modem ---> eth2 Ubuntu eth0----> AT&T Wireless router

```
eth1 will connect to my PC

What im trying to do is setup my Ubuntu Computer as a firewall/router that passes the network into the AT&T Router without touching any packets keeping it unfirewalled.

Problem: I can't get the AT&T router to get a IP using DHCP, I have not tested the PC yet since the Router is my main concern at the moment

If anyone can tell me what info you need for me to post and how to get that info, I will post it.

Excuse me while I go find some rogain

---

### Post by ProjectGod on 2006-07-12
do you mean cable modem...> eth1? 

or is there three ethernet cards on the ubuntu PC?

0 connecting to wireless router
1 connecting to your PC
2 from the cable modem?

correct? which one do you want as the DHCP server?

---

### Post by nalmeth on 2006-07-12
I'm not much a networking wizard, but it seems to me that iptables (the built-in firewall) might be blocking the outgoing connection for you.

You may want to install the firestarter frontend to iptables to configure the ports. You probably know much more about this type of configuration that I do, so I can't help you much further than that.

If you learn anything new and still have difficulties, this problems is probably a little too advanced for the absolute beginners section.

Try the Hardware - Networking area with any new info you get.

Good luck!

---

### Post by Phatie Mcgee on 2006-07-12
> **ProjectGod said:**
> do you mean cable modem...> eth1? 

or is there three ethernet cards on the ubuntu PC?

0 connecting to wireless router
1 connecting to your PC
2 from the cable modem?

correct? which one do you want as the DHCP server?

you are correct, eth0 connects to the wireless router,
eth1 to my PC
eth2 to cable modem

Well I'd like DHCP to feed both my wireless router and my PC, is that possible?

Also, I frogot to mention that I've been trying to get this to work using webmin from this guide [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html")
which I think has only confused me more.. should I start over? perhaps make eth0 cable modem
eth1 wireless router
eth2 PC

any suggestion I am open too.
I'm looking at firestarter now since I want my PC to be firewalled from my Ubuntu box.
Thank you for the quick responses.. from both of you! :)

---

### Post by ProjectGod on 2006-07-12
youre welcome! hmmm :-k hmmmm when you say you want to "feed DHCP to wireless and your PC" does that mean you want to set up your Ubuntu to be a DHCP server dishing out these IPs? :D

if yes, then it gets quite tricky. routers don't like acting as hosts. in other words they're not very friendly to DHCP configuration. you can but you'll have to disable it on the router first and foremost. its likely that by default the wireless is set to DHCP enabled. 

try putting usage of webmin off for a while. try firestarter. i cant give too much details cause i'm at work and am using windows... but i believe firestarter has capabilities to act as a DHCP server and configure for the multiple ethernet cards on the system.

let me know how you fare.

---

### Post by Phatie Mcgee on 2006-07-13
ok I have firestarter installed and kinda setup..

My network is now:
eth0 --cable modem
eth1 --AT&T wireless router
eth2 --PC <-- not working on this yet

under Network settings > eth1 > Properties
Config: Statis IP
IP addy: 192.168.1.105
Subnet: 255.255.255.0
Gateway: blank

In firestarter > prefrences > network settings
(Default gateway=eth0)
Internet device: eth0
Local device: eth1
Enable ICS [X]
Enable DHCP [X]
DHCP Server details:
Create new [X]
Lowest IP: 192.168.1.100
Highest IP: 192.168.1.254
Name Server: <dynamic>

but when I hit accept on that screen I get:
Failed to start the firewall
an unknown error occurred.
Please check your network device settings and make sure your internet connection is active.

While I'm thinking to myself..."ofcourse my internet is active.. im on here right now"...

So im problably thinking wrongly :mrgreen: 


But on the good news..I can get the AT&T wireless router to accept the static IP.. but I cant connect to any website from any of the wireless laptops we have.. so im guessing a DNS problem? how to resolve?

Thanks so much for the help so far, I'm bound and determined to get this working!

---

### Post by ProjectGod on 2006-07-13
hope i dont sound rude... but its still not 100% clear what youre trying to accomplish... please answer see the nifty little diagram i've drawn for your LAN.

if this is spread out it'd be a pretty good setup... something i've done for a client... but if its within one room it quite unnecessary... furthermore if youre just here to test things and see if ubuntu can act as fire wlall / router... then that's a good reason for it too.

anyway. if you plan on using many wireless hosts to attach to the wireless router as in the diag. then you MUST set the wireless router to act as the DHCP server.. so that it can dish out IPs for the wireless clients.

the default gateway for the wireless router must be **eth 1** of the ubuntu machine. DNS for wireless router must also be **eth 1**... the default gateway / DNS for **eth 1** must be **eth 0**... now the default gateway of eth 0 must be the cable modem. 

i'm assuming the cable modem is NOT acting as the DHCP server. if it is the traffic forwarding may not work because eth 0 will continuously have different IPs... although if ubuntu allows you to implicitly specify "eth 0" and not its assigned IP it shouldnt be a problem. to get around this... you can disable DHCP server capabilities on your cable modem / ADSL router and assign it a static IP address.

what i found when i implemented a similar situation was that... on eth0 you'll have to specify its DNS server as your ISP's DNS server address. 

after all this is setup you can start firestarter on each interface and disable it from acting as the DHCP server... you'll have to open up traffic cause firestarter tends to be pretty restrictive. 

furthermore your PC can just have an a STATIC IP. no need for DHCP since there's only 1 pc on that subnet! you'll need a crossover cable for direct nic to nic plug in... o

ne more thing to keep in mind is that each interface will be acting as a separate subnet. therefore eth0 will have to be in the same IP addressing scheme the cable modem assigns its own interface. same rule applies to eth1... it must be assigned an IP within the wireless routers IP scheme. ohhh one more thing you must exclude eth1 's static ip from its DHCP scope when dishing out ips to its wireless host clients.

the other interfaces you'll have to figure out a unique subnet. e.g. if eth0 subnet is 192.168.200.1 / 24. eth1 can be 192.168.201.1 / 24. eth2 = 192.168.202.1 etc... otherwise you can get really clever and try using altered subnet masks like a 26 bit subnetmask for a class c address scheme so that you can save on IP addresses and look absolutely charming infront of your technical friends. hmmm something not recommended if you plan on getting laid. :mrgreen:

let me know how you fare.

---

### Post by Phatie Mcgee on 2006-07-13
> **ProjectGod said:**
> hope i dont sound rude... but its still not 100% clear what youre trying to accomplish... please answer see the nifty little diagram i've drawn for your LAN.

if this is spread out it'd be a pretty good setup... something i've done for a client... but if its within one room it quite unnecessary... furthermore if youre just here to test things and see if ubuntu can act as fire wlall / router... then that's a good reason for it too.

anyway. if you plan on using many wireless hosts to attach to the wireless router as in the diag. then you MUST set the wireless router to act as the DHCP server.. so that it can dish out IPs for the wireless clients.

the default gateway for the wireless router must be **eth 1** of the ubuntu machine. DNS for wireless router must also be **eth 1**... the default gateway / DNS for **eth 1** must be **eth 0**... now the default gateway of eth 0 must be the cable modem. 

i'm assuming the cable modem is NOT acting as the DHCP server. if it is the traffic forwarding may not work because eth 0 will continuously have different IPs... although if ubuntu allows you to implicitly specify "eth 0" and not its assigned IP it shouldnt be a problem. to get around this... you can disable DHCP server capabilities on your cable modem / ADSL router and assign it a static IP address.

what i found when i implemented a similar situation was that... on eth0 you'll have to specify its DNS server as your ISP's DNS server address. 

after all this is setup you can start firestarter on each interface and disable it from acting as the DHCP server... you'll have to open up traffic cause firestarter tends to be pretty restrictive. 

furthermore your PC can just have an a STATIC IP. no need for DHCP since there's only 1 pc on that subnet! you'll need a crossover cable for direct nic to nic plug in... o

ne more thing to keep in mind is that each interface will be acting as a separate subnet. therefore eth0 will have to be in the same IP addressing scheme the cable modem assigns its own interface. same rule applies to eth1... it must be assigned an IP within the wireless routers IP scheme. ohhh one more thing you must exclude eth1 's static ip from its DHCP scope when dishing out ips to its wireless host clients.

the other interfaces you'll have to figure out a unique subnet. e.g. if eth0 subnet is 192.168.200.1 / 24. eth1 can be 192.168.201.1 / 24. eth2 = 192.168.202.1 etc... otherwise you can get really clever and try using altered subnet masks like a 26 bit subnetmask for a class c address scheme so that you can save on IP addresses and look absolutely charming infront of your technical friends. hmmm something not recommended if you plan on getting laid. :mrgreen:

let me know how you fare.


Rude? not at all! all the help you have givem me is very consiterate! and that diagram is really cool :mrgreen: indeed you are living up to your name!

I've also relized that I dont think I have a crossover cable.. I'll have to find some diagram and see what it looks like 

and.. bad news :(  The family has has expressed concerns about the reliablity of this network setup.  Even after telling them linux is stable and this would be better... they dont want it to happen, and since its my fiances family which I live with, I have to heed thier concerns in this matter :(

So what I did was set the router to have a DMZ on the interface which is going to my Ubuntu box.. hopefully this will work out good.. because this router really sucks and I hate opening ports on it everytime I want to try somthing new :) 

So I now have my Ubunut box getting internet from the router.  Ubuntu is connected to my PC and will firewall it.  BUT my network cards eth1/2 are not working now! eth0 is still connected fine and working. but the nic that is connected to my PC is not lighting up.

For the life of me I am throughly confused beyond reason.

On the same note, I will be using this setup that you have explained in detail when we move out in September.. since it will only be my fiance and me :) and her wireless laptop.

So thanks again for detailed information and diagram, I will use it!

Now off to find what I screwed up.. ](*,)

---

### Post by ProjectGod on 2006-07-14
almost forgot... makes life alot easier rather than manually editing IP tables... get a GUI tool. there's quite a few...

research... try:

Shorewall.

you can grab this from synaptic.

in-laws. hmmm they're always getting in the way of fun yeah? ;)

cheers

---

