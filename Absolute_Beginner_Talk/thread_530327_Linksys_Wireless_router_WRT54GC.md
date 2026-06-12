---
title: "Linksys Wireless router WRT54GC"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-08-20
Hi,

Just bought the above router, no problems logging in with cable .... but it has no connection for phone

Could I use spare network connection on my desktop to share with wireless router?

This thing is more like a network hub ... guess I have bought the wrong thing [again!]

If I can make use of it would be handy

TIA

MrG

---

### Post by asmoore82 on 2007-08-20
> **MrGreen said:**
> Just bought the above router, no problems logging in with cable .... but it has no connection for phone

[SIZE="7"]:confused:[/SIZE]

---

### Post by mstephens on 2007-08-20
Basically a wireless router will normally have an RJ45 connection for Ethernet  10/100 Base T which goes to  a matching socket on a Cable Modem or whatever piece of kit you use to connect to the big wide world.  If you have any form of Broadband connection it should be possible to plug this into the wireless router. Most wireless routers also have a few wired connections (again RJ45) which you could then use to plug whatever was previously connected direct to broadband (your desktop?) into the router. 

If you only have a traditional slow modem which is currently plugged into (or forms part of ) your desktop PC, you could connect the desktop ethernet port  into the wireless router (use the port which should go to a wireless modem)  so that you are connected to the Internet via the desktop PC (which would need to be switched on all the time). Note that this would be pretty slow for everyone AND you will need to configure the PC to forward packets onto the internet.

If the desktop is running Ubuntu, there should be something round here which tells you how to do it. If it's running Windows, the connection wizard might help (or it might not!).    

Easy solution if you don't have Broadband already is to get it and make sure that whatever bit of kit you buy ( or are supplied with)  can connect to your new  router.   

Oh and you could have Linux running on the router as well if you want. Google DD-WRT for more info

---

### Post by MrGreen on 2007-08-20
Thanks for the heads up, I have a broadband router atm never had a problem with it only would have liked wireless

Like you say running through pc is going to slow it down

Have to have a rethink 

thanks again

MrG

/me searches forums

---

### Post by mstephens on 2007-08-21
Slightly confused now.

Doesn't your ATM router have Ethernet LAN ports ? If it does just plug the wireless router WAN port into an ATM router LAN port. If there is only one and your desktop is currently using it, the PC just connects into one of the wireless router LAN ports instead.

---

### Post by DeusEx on 2007-08-21
can you find out what version of hardware it is? the one I used to have was a V7 and a piece of crap.

---

### Post by MrGreen on 2007-08-21
Yeah I could plug my router into it, but did not see the point of running two.... 

There are 4 ports on Linksys so one could connect to router, my desktop does have wireless onboard or I could just connect it via ethernet cable

If I can get my head round it  lol

Thanks for all your help

MrG

---

### Post by blowinsmoke on 2007-08-21
I just got off the phone with Linksys and they advised me that Linksys does not support the Linux OS.   I was trying to use Ubuntu on my wireless network.  I have a WRT54G router.

Guess that I will have to change routers.

Ken

---

### Post by Austin_KW on 2007-08-21
> **blowinsmoke said:**
> I just got off the phone with Linksys and they advised me that Linksys does not support the Linux OS.   I was trying to use Ubuntu on my wireless network.  I have a WRT54G router.

Guess that I will have to change routers.

Ken

You need to understand what they are telling you. The mean that they will not give you Support in using linux with the router. Heck, The thing was developed using linux and you can load linux back onto it. 

It just means that their support people are clueless, not that it does not work.

---

### Post by Jimmyfj on 2007-08-21
I have a Linksys WRT54GL wireless router with 4 ports and it works flawlessly with my Ubuntu, 2 x 7.04 Feisty and 1 x 7.10 Gutsy 64-bit. Both the wireless part and the cabled part are working just fine. I just had to update the firmware to be sure that I got the newest version and I'm satisfied. I use it with a Siemens high speed ADSL modem and have had a second router set up as well without issues.  Linksys is known to support hardware on Linux just fine.

---

### Post by Austin_KW on 2007-08-21
> **MrGreen said:**
> Yeah I could plug my router into it, but did not see the point of running two.... 

There are 4 ports on Linksys so one could connect to router, my desktop does have wireless onboard or I could just connect it via ethernet cable

If I can get my head round it  lol

Thanks for all your help

MrG
Two options
1. Routing;
Connect the WAN ethernet port of the linksys to one of the lan ports on your broadband router. Add the linksys to the DMZ of your broadband router using its web interface. 
Connect everything else to the linksys (wired/wireless) and forget the broadband router is even there.

2. Bridging;
Connect a PC to the linksys and disable dhcp server using the web interface.
Connect one of the LAN port of the linksys to one of the lan ports on your broadband router. 
Connect everything else to either the linksys (wired/wireless) or the broadband router (wired), it does not matter as everything is bridged together on the LAN

---

### Post by mstephens on 2007-08-23
Bottom line is that you need to have both boxes powered up and connected in some way - the wireless router will only have Ethernet ports so it needs to connect to something else which has them.

Referring back to the guy who was told that Linksys don't support Linux: 

What model of router you have or haven't got should not affect what OS is being run on the PCs connected via the router or what OS the router itself runs. Wired connections should never be a problem (ethernet is ethernet) and wireless ones might only be a problem if the type of connection is a non-standard i.e. not 802.11b/g or if the OS doesn't have available drivers which support WPA or the like.

---

