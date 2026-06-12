---
title: "Sharing internet betwween laptop/desktop"
date: 2005-04-27
forum: Apple PPC Users
---

### Post by Rxke on 2005-04-27
In OSX, there's a simple, menu-clickety-click, way to connect a laptop, which uses an airport card for internet access, wit an ethernet cable to a desktop (or other laptop) so that that second computer can share the internet connection through the laptop.

I guess that's perfectly possible with Linux too, but how?

I have a desktop without net connection, and am not allowed to drill holes in the walls/ceilings to connect it to the accesspoint, which is a hssle.. So I would like to use my laptop as errr... 'inter-connector' to the net, but I can't figure out how. Should the laptop function as some kind of server or... Confusion in newbieland, heh.

(I hope this mumbo-jumbo Eglish of mine makes any sense....)

---

### Post by hobnob on 2005-04-27
Hi Rxke,

Yes, this is easily achieved under Linux. What you need (and how your Mac did it) is to use a feature called NAT or Network Address Translation, which is built into the Linux kernel. You have complete control over the routing using tools such as iptables, but there are many programs out there that do most of the hard work for you.

To get you started, have a look at [Firestarter](http://www.fs-security.com/) and in particular, their page on [connection sharing](http://www.fs-security.com/docs/connection-sharing.php). Another alternative would be [Shorewall](http://www.shorewall.net/) which many people like. Regardless, it shouldn't be too painful to set up and there are many documents out there to help you when you get stuck! Try searching for [IP Masquerading](http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/).

As a final point, have you considered buying a wireless adaptor for your desktop PC? They're getting very cheap, just make sure you check it is Linux compatible before you hand over your hard earned money.

Let me know how it goes!

---

### Post by Rxke on 2005-04-27
Thank you very much, hobnob! I'll go and check it out.

[QUOTE=hobnob]point, have you considered buying a wireless adaptor for your desktop PC? They're getting very cheap, just make sure you check it is Linux compatible before you hand over your hard earned money[/QUOTE]

Heehee, you should see the pile of cheap trash i'm running my stuff on... all half-broken, second or third hand material, too stingy to buy stuff, if I can get around gutting older trashed machinery. I know a simple USB wireless adaptor or something similar would do this stuff, but I happen to have some cheapo ethernet cables lying around, and figure it could be workable that way too...

---

### Post by hobnob on 2005-04-27
Hehe, a true geek : ) Good luck with the above.

---

### Post by Rxke on 2005-04-27
Yay, done!

Thanks to the links you supplied it was indeed a piece of cake.

Some notes, though: 

be sure to apt-get install dhcp ! I thought it was already installed, but it was not, which lead to some headscrathing why oh why dhcp didn't work, heh. Having struggled with DHCP under Debian, I reallly thought it was standard etc etc...

Can be confusing: eth0 is your Airportcard, eth1 your ethernetport, keep that in mind when reading the how to at the firestarter pages, they use another default, eth0 being external etc....

thanks again, hobnob, it's a great feeling, seeing my desktop doing an update, using my crummy first gen iBook, yeehaa!

---

