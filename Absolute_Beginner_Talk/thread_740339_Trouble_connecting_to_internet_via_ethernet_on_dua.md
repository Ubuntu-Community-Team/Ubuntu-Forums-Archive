---
title: "Trouble connecting to internet via ethernet on dual boot"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by emptybox on 2008-03-30
I just installed Ubuntu 7.10 as a dual boot on a desktop machine that was running XP Home.
It connects to the internet via an ethernet cable running to a wireless adsl modem/router.

This connection was running fine on XP before I installed Ubuntu, however I cannot get it to connect to the internet at all now, either through Ubuntu or XP. :confused:

I have tried rebooting both the router and the computer several times to no avail. I have also diconnected and reconnected the cable and made sure there are green lights either end.
Also I have taken the cable out of the back of the computer and connected it to my iBook laptop (after disabling the wireless), and it connects to the net without any problems, so i assume it is something in the computer rather than the cable or router.

It seems to have some comunication with the router. It has assigned it an IP address that is different to what the computer had before, and there is some incoming and outgoing traffic, but I cannot bring up the router's configuration page in Firefox (or IE in XP), and I cannot connect to the net.

Here is the result of ifconfig
................................................................
eth0      Link encap:Ethernet  HWaddr FF:FF:FF:FF:FF:FF  
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::fdff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8603 (8.4 KB)  TX bytes:12220 (11.9 KB)
          Interrupt:16 Base address:0x2800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
...............................................................................

And here is the result of dhclient
...................................................................................
Listening on LPF/eth0/ff:ff:ff:ff:ff:ff
Sending on   LPF/eth0/ff:ff:ff:ff:ff:ff
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.11 -- renewal in 40354 seconds.
......................................................................................

I have a variable external IP address.

I have tried various things from other threads.
I set ivp6 in Firefox to True, but that had no effect.

I have also tried setting the wired network connection to 'Roaming' and also the  manual configuration to DHCP.
Nothing has made any difference. 

I'm utterly baffled. I can't see why a simple ethernet connection doesn't just work, and I certainly can't see why it would affect the XP install??? :confused:

Has anybody got any ideas?

---

### Post by markharding557 on 2008-03-30
can you connect the computer directly without the router to see if this works we will know then if the router is the problem

---

### Post by emptybox on 2008-03-30
> **markharding557 said:**
> can you connect the computer directly without the router to see if this works we will know then if the router is the problem

By what method?
I have got an old USB modem I could try but I doubt that would work in Ubuntu?
Could give it a try though.

I do have suspicions about the router, and in fact file sharing seems to have gone a bit funny, I'm sometimes being told I haven't got permission to access a share where I could access it before, but as I said, I was able to connect without any problem using my laptop through the same cable? :confused:

I've got another XP machine and another Ubuntu desktop connecting wirelessly through the router, and they have no problem getting on the internet.

I'll go and dig out that USB modem and see if I get anywhere.

_Edited to add:_
I set up my old Speedtouch modem, and was able to connect to the internet with it no problem in XP (it wasn't recognized in Ubuntu)
Not too sure what this means, except that there's nothing in the computer blocking it from the internet, but the ethernet port could still be the problem.

I'll try some more experiments another day.
I'll take one of my other desktops downstairs and see if they can connect via the ethernet cable. Also I have an Orange Livebox router that I've never used. As a last resort I'll set that up and try and set up the network using that. :eek:

Am I right in thinking that because both the XP install and the Ubuntu is affected, then that points to hardware? Because configuring one shouldn't affect the other?
Having said that the router** did** assign a new IP address to **both** installs when I put Ubuntu on.

In the mean time if anyone has any ideas please put them on this thread, and I'll check back at intervals. :)

---

### Post by louieb on 2008-03-30
When you quit xp do you hibernate it? sometime that will put the network card to sleep too. But that doesn't explain why its not connecting in XP.  

My wild as guess of the day Hardware. Try another NIC.

---

### Post by emptybox on 2008-03-30
Hi louieb. :)

No I never hibernate, just shut it off completely (well soft shut off or whatever it's called. I don't turn it off at the plug).

I haven't got another ethernet card to try, all my other machines have it on the motherboards, but I **will** try another machine on that cable, just to be sure.

I've got a PCI wireless card in this machine (Ubuntu), I could swap that into the Dell (the troubled machine) as an experiment?
Have to be another day though.

---

### Post by emptybox on 2008-03-31
As a postscript to this, I bought my other Ubuntu desktop down and connected it up to the ethernet cable and it connected straight away to the internet. No adjustment or configuration required, so I think I can safetly say that it is an issue with the dual boot computer. Most likely the ethernet card has developed a fault.

I will try to connect the computer wirelessly and see if that works.

Only other thing is that I haven't had a dual boot machine before.
Is it possible that it has confused the router in some way?

Does the router see it as two different computers or just the one machine?

It seems to assign one IP address to both installs, or is the IP address assigned to the physical connection, i.e. the ethernet card?
As I said in an earlier post, as soon as I tried to connect via Ubuntu the router assigned a new IP address to the computer.

---

### Post by Duck2006 on 2008-03-31
> Does the router see it as two different computers or just the one machine?

It seems to assign one IP address to both installs, or is the IP address assigned to the physical connection, i.e. the ethernet card?
As I said in an earlier post, as soon as I tried to connect via Ubuntu the router assigned a new IP address to the computer.

The router see the system as one, you can only boot linux or windoze so it's only got to see witch OP is booting.

The router just gives the assignes  line an ip address, so it does not matter what you boot it is the same ip.

---

### Post by ugm6hr on 2008-03-31
Definitely points to a hardware issue.

From your experimentation - likely with the NIC, since router and cable seem OK.

---

