---
title: "static ip?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by steelmole on 2008-04-21
How do I get a static ip, so I can forward ports from my router to my computer?  My router has an ip address of 192.168.1.1  

I tried changing my computer to static ip but I couldn't even access the router like that.

---

### Post by aktiwers on 2008-04-21
```
ifconfig
```

Shows your IP.

Then go through firefox, to your router and forward the port as usual, to your IP from ifconfig.Its the one called "inet addr:"

---

### Post by steelmole on 2008-04-21
But if I don't have a static ip that ip adress won't always be this computer.  But then I set a static ip address and nothing networky seems to work.

---

### Post by Confuzius on 2008-04-21
Try setting it to something odd or higher, if there are other computers on the network that are not set to static ip also you might be getting interference from them, try something like 192.168.1.57 or something random.  It took me some trial and error to get one that worked.

---

### Post by aktiwers on 2008-04-21
I don't quite understand?
Sorry if I am being ignorant here, but the IP address from the router is internal and not static? And your other IP, like the one shown here:
[http://whatsmyip.org/](http://whatsmyip.org/)

Is static.

But to forward ports you need the internal one, and it should not be static.

Did I misunderstand you?

---

### Post by Barrucadu on 2008-04-21
You will need to configure your router to assign you a static IP.

---

### Post by steelmole on 2008-04-21
> **aktiwers said:**
> I don't quite understand?
Sorry if I am being ignorant here, but the IP address from the router is internal and not static? And your other IP, like the one shown here:
[http://whatsmyip.org/](http://whatsmyip.org/)

Is static.

But to forward ports you need the internal one, and it should not be static.

Did I misunderstand you?

I want my computer (on a local network) to have a static ip, so my router can forward ports to it.  When I try to set up a static ip I lose any internet connection or network connection to my router.

I've dived into the router settings and can't see much.  Any clues one what to look for?

---

### Post by Confuzius on 2008-04-21
It's static vs DHCP, I don't think it actually has anything to do with the router.  You can change it locally by clicking on the network connections icon and choosing "manual networking settings" (something like that, I'm at work now and can not be 100% sure, going from memory)

---

### Post by Tatty on 2008-04-21
> **Confuzius said:**
> It's static vs DHCP, I don't think it actually has anything to do with the router.  You can change it locally by clicking on the network connections icon and choosing "manual networking settings" (something like that, I'm at work now and can not be 100% sure, going from memory)

Yes do this, then after you do that there may be a page in your routers configuration where you can tell it if you have any static ip's on your network.  This is not essential i dont think, but it prevents it giving that address to another machine by mistake.

---

### Post by gug@fnal.gov on 2008-04-21
I just posted about getting ssh to work a few days ago. Turned out I needed to go into the system administration tool for network. I am not home and so am sitting at a RHEL instead of Ubunto system so I cannot give you extact menu item spellings. But it is something like, system->administration->network. Anyway when you get there, you need to unclick the Use Roaming checkbox and then enter the new IP information. 
 
I have noticed that on my old DLink router the guide said something like the first N addresses are DHCP, so I could easily choose an address above that. I don't recall that mentioned in my Linksys guide, but I just chose something above 150, e.g. 192.168.1.181 and that pattern works. I have three different systems using static IPs at home (one printer, one network attached storage, one desktop) and it required no changes to the router. 

If I remember correctly, once you switch off the roaming and save the changes it re-initializes the network automatically. 

Good luck.

---

### Post by banished_one on 2008-04-21
dont you need to request static ip from your internet service provider and you even pay a small amout to make that change, am i wrong :S

---

### Post by steelmole on 2008-04-21
I do that, change that stuff, pick an ip that is out of the range of my DHCP but it doesn't work.  Here what ifconfig gives me:
```
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:55:b5:86  
          inet6 addr: fe80::21a:4dff:fe55:b586/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:591292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:477442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:642541479 (612.7 MB)  TX bytes:76463282 (72.9 MB)
          Interrupt:252 Base address:0xa000 

```

---

### Post by andrew.46 on 2008-04-22
Hi,

 I have just setup what you are talking about. Starting from the top:

------------ Externally --------------

1. My ISP assigns me an IP address which is variable.
2. I have signed up with dyndns.org who generate an IP number each time my address changes and then link it with myaddress.dyndns.org
3. I have set my router to alert dyndns.org each time this address changes.

---------- Internally ------------------

1. I have a computer attached to the router which uses DHCP.
2. The router is set to give this computer the *same* address each time.
3. I have set port forwarding (22) to this computer for ssh.

----------------------------

Is that clear? It helps to have a good router that will do some of this magic for you. Mine is a Speedtouch 585, great piece of hardware.

     Andrew

---

### Post by steelmole on 2008-04-22
Well, it makes sense but I just can't find anything in the linksys router about setting a static ip. When I did this with windows setting the computer to just have a static ip was enough.

---

### Post by andrew.46 on 2008-04-22
Hi:

> **steelmole said:**
> Well, it makes sense but I just can't find anything in the linksys router about setting a static ip. When I did this with windows setting the computer to just have a static ip was enough.

Strictly speaking it is not a static IP, the computer still asks for any IP number availabe (DHCP) it is just that the router holds one especially for this computer. Static IP would be the computer asking for a specific IP and the router providing this. A fine point.

    Andrew

---

### Post by steelmole on 2008-04-22
So, no progress then.  I've no clue how to get my router to give the same ip address each time.

And setting a static ip on the computer just breaks any kind of use of the network.

---

### Post by aktiwers on 2008-04-22
The router should give you that by default. Sorry I was not clear in post #5, but this is what I meant. That the router gives you the same IP all the time and the one you connect to the internet with can be Static. 
If you did order this from your ISP (static IP), then I guess it should work.

When you set it to static ip in Ubuntu, can you then ping your router? 
(in terminal type)

```
ping 192.168.1.1
```

If so, this is not a router problem. Then I would guess your ISP didn't give you a Static IP yet, and you should call them.

---

### Post by andrew.46 on 2008-04-22
I can see that you are going to get a little bit of contradictory information on this one. It can be done though, I attach a screenshot of the relevant section of my own router setup.

You will see that the computer slackware-desktop is on eth4 and it connects by DHCP to the router but the router always gives it the same address. AT the bottom you will see where I have set port forwarding to allow ssh requests on a certain port (22) to go to this computer.

I am no computer genius and if I can do it I suspect that you can too.

    Andrew

---

### Post by apostate on 2008-04-23
> **Confuzius said:**
> It's static vs DHCP, I don't think it actually has anything to do with the router.  You can change it locally by clicking on the network connections icon and choosing "manual networking settings" (something like that, I'm at work now and can not be 100% sure, going from memory)

Ok,

If you are trying to set up a server, you need a static *public* IP.  This is a difficult requirement for home users, but can be circumvented in a number of ways. Take a look at [http://no-ip.com](http://no-ip.com)

Now, as to your private address, you will need to get your gateway and computer to agree on what your static IP is to be, and if it is giving you trouble, consider just leaving it as DHCP. You should get a semi-permanent lease on a private IP, as in a home network there is no real reason for it to re-assign addresses unless you change the cable-plant or hardware configuration. This box I am using for instance is in DHCP mode, but I've had 192.168.0.3 for ever and ever. It never changes, as there are not many resources competing for addresses in my house!

Just leave it DHCP, and forward the ports. If you have to change the forwarding once or twice a year, it's not a big deal. 

:-)

---

### Post by steelmole on 2008-04-23
No I'm not trying to get a static public ip. 

As far as I can tell my router doesn't have any options for setting a specific device to have the same ip all the time.

And it's a right pain to change port forwarding all the time, whenever someone happens to be using another computer or a laptop etc.  That's why I want a static ip.  I shouldn't have to just live with a setting that doesn't work.

---

### Post by apostate on 2008-04-23
> **steelmole said:**
> No I'm not trying to get a static public ip. 

As far as I can tell my router doesn't have any options for setting a specific device to have the same ip all the time.

And it's a right pain to change port forwarding all the time, whenever someone happens to be using another computer or a laptop etc.  That's why I want a static ip.  I shouldn't have to just live with a setting that doesn't work.

Why would you have to change it all the time?  What exactly are you trying to accomplish with this?

---

### Post by steelmole on 2008-04-23
Because my computer gets given a different ip depending on when computers were switched on etc.

---

### Post by apostate on 2008-04-23
> **steelmole said:**
> Because my computer gets given a different ip depending on when computers were switched on etc.

Well, you definitely don't want to assign yourself an ip that is within the range of DHCP addresses. You may need to configure the range of dynamic addresses to be more limited, as you can't use a static IP (or shouldn't) from this same pool of addresses.

It should be on the same subnet of course, (192.168.0.) or whatever the other PCs are on.  Without knowing more about your hardware, I am not sure I can help much more.

---

### Post by steelmole on 2008-04-24
It's a linksys BEF11S4 router.  I set the subnet mask to 255.255.255.0 same as the others.  I picked an ip address outside of the DHCP range.

---

