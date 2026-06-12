---
title: "Failed to connect to internet"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by amit on 2006-06-05
Hi...
I am a begineer in the world of ubuntu.
I am facing some problems in conneting my system to the net.
I have tried, almost all the options to make internet work on ubuntu but somehow failed :(.
My system is connected to internet thr a cable, ...pugged in directly to 
my systems ethernet card.
I have activated my eth0 and did all the settings e.g putting static i.p, subnet mask..gateway..DNS server etc, by navigating to
 system->Administraton->networking.

But that did'nt work at all.....
Please help me out ..

Thanks in advance

Regards,
Amit

---

### Post by joshrobinson on 2006-06-05
[QUOTE=amit]Hi...
I am a begineer in the world of ubuntu.
I am facing some problems in conneting my system to the net.
I have tried, almost all the options to make internet work on ubuntu but somehow failed :(.
My system is connected to internet thr a cable, ...pugged in directly to 
my systems ethernet card.
I have activated my eth0 and did all the settings e.g putting static i.p, subnet mask..gateway..DNS server etc, by navigating to
 system->Administraton->networking.

But that did'nt work at all.....
Please help me out ..

Thanks in advance

Regards,
Amit[/QUOTE]

is your computer hooked into a router? or is the modem hooked directly into your computer?
if you are running a router, have you tried putting it on dhcp? it could work both ways.

i would try putting your network adapter on DHCP instead of static, then opening a terminal, applications >accesories>terminal
and typing this command

```
sudo dhclient 
```
if it says something like "bound to xxx.xxx.xxx.xxx" you should be good to go

---

### Post by deadgobby on 2006-06-05
Here is a simple thing to try. Turn off your modem, if you have a router. Turn that off too. Power down your Dapper box. Wait at least on minute before powering up the modem and Router. Let the modem do the self test and same with the router. After the self test. Turn on the modem if not on. Boot up Dapper with the modem on. If the modem is off or you turn it on after Dapper boots up. Dapper does not see any connection for some reason. Booting up with the modem on may solve this.
Gobby

---

