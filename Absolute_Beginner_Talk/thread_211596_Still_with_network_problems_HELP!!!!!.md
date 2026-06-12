---
title: "Still with network problems HELP!!!!!"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by cyberlite on 2006-07-08
Hey all

I still can't get on the net with ubuntu, after installing this morning I,ve been reading all the thread with the same pro but no luck.](*,) I,ve tryed every thing but nothing

Any help?????

---

### Post by annda on 2006-07-08
please describe your problem.

what type is your modem and how do want to connect? dial-up, cable, wireless, usb, built-in etc. those are the first things you sould tell us. the name of the device could also be useful.

---

### Post by krpnm on 2006-07-08
It would be quite helpful if you would thoroughly describe:

a. What kind of Internet connection you have (modem, ISDN, DSL, etc.)
b. What kind of error you are receiving
c. Are you going through a NAT, router, proxy?

Anything else to isolate the problem.

---

### Post by cyberlite on 2006-07-08
Ok so here gos

In I have a duel boot machine and under xp all works ok I have internet, But under ubuntu not.

In ubuntu I have assign it a static ip from the router just like in xp, Now here the thing if I reboot the os I have internet for a sencond or two.
With the network tools I see its using ipv4 so thats ok, I,m at a loss guys...............................:confused: 

I do have a Davicom network card I think there is the problem, maby a driver prob or so????

---

### Post by annda on 2006-07-08
sorry, i have absolutely no experience with static IP so i don't know if that's a factor or not (like DHCP issues or something). can you connect to your router though? or no connection whatsoever?

have you tried pinging in the terminal window?

---

### Post by John.Michael.Kane on 2006-07-08
Have you tried connecting with out the router? atleast this will weed out the router as the hick-up.

---

### Post by krpnm on 2006-07-08
Have you tried a modprobe for eth0 (I'm assuming you only have one NIC)?

Secondly, if the module for your NIC is successfully loaded you can do a ping 127.0.0.1 (local host or loopback).  Use ctrl+c to stop the local ping if it works.

Third, located in the /etc/network directory you should find the "interfaces" file.  Open it and you should see something like this:

# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.1

Your static IP address, netmask and gateway maybe different.  Why don't you post it?

---

### Post by cyberlite on 2006-07-08
autolo
iface lo inet loopback

# primary netwok interface
auto eth0
iface eth0 inet static
address 192.168.2.23
netmask 255.255.255.0
gateway 192.168.2.1

I think this is all ok, but something is stopping the comunication between pc and router.

---

### Post by cyberlite on 2006-07-08
ping 127.0.0.1 was ok

---

### Post by cyberlite on 2006-07-08
The problem was with the [COLOR="red"]davicom[/COLOR] networkcard utuntu has a problem with it. I google it and found that to be the problem. I had a realtek networkcard installed it and vuala I have very fast internet, faster then may XP\\:D/ 

Davicom:evil: the hole day shoot because of card, ho well live(linux) and learn.:D :D :D :D

---

