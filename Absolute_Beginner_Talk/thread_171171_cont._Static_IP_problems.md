---
title: "cont. Static IP problems"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by N3wtR0ckn13 on 2006-05-06
TheProbleM:
I'm having static ip problems again. can't resolve a connection whatsoever. 
----------------------------------------------------------------------------
NeTworKLoG:

/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.1.1  //changed from 192.168.0.1 to match my linksys router
--------------------------------------------------------------------------
ThingsIhaveTried: 
i have not set up iptables yet, so i'm not behind a firewall. i've port forwarded http port 80 in my router just in case. i've also configured my win xp system with the same static configuration just to test the connection. only my chat client was able to connect. 
-------------------------------------------------------------------------
TheSetuP:
linksys router > netgear switch > ubuntu server
-------------------------------------------------------------------------
YOU: 
need suggestions. thx.
-------------------------------------------------------------------------

---

### Post by Sendervictorius on 2006-05-06
can you successfully ping your router port?

---

### Post by souki on 2006-05-06
[quote=N3wtR0ckn13]
# The primary network interface
auto eth0
iface eth0 inet static
**         address 192.168.0.100**
**         netmask 255.255.255.0**
        network 192.168.0.0
        broadcast 192.168.0.255
        **gateway 192.168.1.1**  //changed from 192.168.0.1 to match my linksys router
[/quote] you are on the 192.168.0.0 with a netmask 255.255.255.0
that means your router is not on the same network (there is no route to the gateway !!)

- revert back your gateway to 192.168.0.1 and set your linksys router with this adresse
- or keep linksys like this and change all your address from 192.168.0.* to 192.168.1.*

---

### Post by N3wtR0ckn13 on 2006-05-06
[QUOTE=Sendervictorius]can you successfully ping your router port?[/QUOTE]

can't ping, 100% packet loss.

---

### Post by N3wtR0ckn13 on 2006-05-06
[QUOTE=souki]you are on the 192.168.0.0 with a netmask 255.255.255.0
that means your router is not on the same network (there is no route to the gateway !!)

- revert back your gateway to 192.168.0.1 and set your linksys router with this adresse
- or keep linksys like this and change all your address from 192.168.0.* to 192.168.1.*[/QUOTE]

this isn't very clear and even if i got what you were saying it didn't work, but thanks. 

as far as i know, it shouldn't matter if my router is setup as a dhcp server. my server is only local anyways. their is a option however that know little about on wrt54g v3 that you can configure a static ip with the dhcp running. nevertheless, i am totally lost now. what needs to match up on my server when compared to the router?

---

### Post by N3wtR0ckn13 on 2006-05-07
[QUOTE=N3wtR0ckn13]this isn't very clear and even if i got what you were saying it didn't work, but thanks. 

as far as i know, it shouldn't matter if my router is setup as a dhcp server. my server is only local anyways. their is a option however that know little about on wrt54g v3 that you can configure a static ip with the dhcp running. nevertheless, i am totally lost now. what needs to match up on my server when compared to the router?[/QUOTE]

linksys Wrt54g router static configuration. Ubuntu server w/ static ip. the connection type in the linksys router must be set to STATIC IP inorder for this to work. hillarious as this might sound, it's not that obvious since network setup also designates dhcp. the confusion came when i was trying to route my network so that my server could utilize a designaited connection. also the range of the dhcp was opposite what alot of others had commented on. i appreicate it nevertheless. in this linksys wrt54g, you can enable dhcp to run without any problems while providing a static ip connection. the problem was understanding which one was the primary connection in the setup. you can enable and disable both. 

thanks for all the suggestions. peace.

---

