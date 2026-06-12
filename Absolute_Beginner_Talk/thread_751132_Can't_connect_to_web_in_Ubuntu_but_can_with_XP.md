---
title: "Can't connect to web in Ubuntu but can with XP"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by must4rdgas on 2008-04-10
Hi all,

In Windows my LAN always has "little or no connectivity", but I can still connect to the web. I use a DSL router in bridge mode and enter my DSL account details manually. The other PC that connects to the router has no LAN problems - could be my LAN cable.

In Ubuntu on my PC, after finding two devices with pppoeconf and scanning, I get a "no pppoe access controller" error, so I cannot enter my DSL account details and connect.

If I can connect in Windows, surely there must be a way to connect in Linux. Something like setting up the DSL account beforehand, as with "Create new connection" in Windows.

Any ideas?

Thanks,

must4rdgas.

---

### Post by TeoBigusGeekus on 2008-04-10
System->Administration->Network
Have you been there?

---

### Post by must4rdgas on 2008-04-10
Yip, been there.

I actually seem to have fixed the "little or no connectivity" in Windows by changing some of the TCP/IP settings.

I entered the same settings in System > Administration > Network, but still nothing.

P.S., it's "access **concentrator**", not "access controller"...

I'm sure it's not an Ubuntu problem, but seeing as Windows can connect to the net, there must be a way to connect with Ubuntu!

---

### Post by fourscore on 2008-04-10
what is the network card you have ?

---

### Post by TeoBigusGeekus on 2008-04-10
In the same dialog box, in the connections tab, click the properties of the wired connection and enable roaming mode.

---

### Post by must4rdgas on 2008-04-10
Roaming mode doesn't work. Removes the IP addreses I added to try and configure.

I know my router has DHCP enabled. I've tried all the settings - Static mode, DHCP mode, ip4.

---

### Post by must4rdgas on 2008-04-10
Well I followed [this](http://ubuntuforums.org/showthread.php?t=538448) and have managed to get the no connectivity light to disappear on my DSL router, so now all is well on the router side.

I've set up the connection in Ubuntu on my PC exactly the same as on this PC (which runs Ubuntu and Windows) but still no Internet. :(

---

### Post by must4rdgas on 2008-04-10
Anyone? :(

---

### Post by must4rdgas on 2008-04-11
Last bump and then I give up. :(

---

### Post by caravel on 2008-04-11
Any particular reason why you're using a DSL router in bridged mode?  What router do you have?

---

### Post by must4rdgas on 2008-04-11
Mainly for downloading and not having to foward ports manually.

It's a Billion 5100, rebranded.

I think it's a problem with the Gigabit LAN...

---

### Post by bumanie on 2008-04-11
It could be the LAN, but have you tried disabling ipv6 in firefox? I could not connect to the internet with 7.10 until I did this.

---

### Post by must4rdgas on 2008-04-11
@bumanie:

I have not tried that. Don't think I've gotten there yet. I'm still trying to configure my router in pppoeconf. Would I need to disable ipv6 in Firefox yet?

I've tried every thread here. Saw some info about disabling ipv6. Another fix is enabling 'Wake-on-LAN' on the network card in Windows. Mine has always been enabled.

---

