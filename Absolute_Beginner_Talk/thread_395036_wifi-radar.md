---
title: "wifi-radar"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Tunica Intima on 2007-03-27
I just installed wifi-radar after giving up on network manager, but now I just can't get an ip address. What do I need to check to start troubleshooting this?

---

### Post by kerry_s on 2007-03-27
Man, this wireless in feisty just sucks. I'm trying to get this laptop ready for travel. Like you the wireless just refuses to connect even though there's like 16 open connections. I didn't have no luck with wifi-radar to, i ran the "sudo wifi-radar" a ton of times. i can see the connections just can't connect. It's really pissing me off. :confused:

---

### Post by Falados on 2007-03-27
i don't use Fiesty, but on Edgy i've been using nm-applet to connect to wireless networks... Try that?

---

### Post by kerry_s on 2007-03-27
> **Falados said:**
> i don't use Fiesty, but on Edgy i've been using nm-applet to connect to wireless networks... Try that?

Yes, feisty uses the same nm-applet, it sucks. Edgy my wireless doesn't even work. I'm using a blitz usb wireless key(zd1211 chip).

I guess it's time to go shopping. :)

---

### Post by Mongoose on 2007-03-28
Yeah, I was using LTS and edgy on a laptop and both worked fine with the 3 wireless cards I use.  Feisty seems to have broken DHCP with wireless and with some kernel package revisions the drivers are broken (or missing) as well.  Both wifi-radar ( which I like for browsing APs also ) and the networking GUI didn't work for me even with working ( native linux ) drivers.  I noticed nothing I set in either actually affected my wireless device as shown by iwconfig.

I ended up manually configuring my most used card, which is a DWL-G650:

iwconfig ath0 essid ACCESSPOINTNAME key WEPKEY

ifconfig ath0 192.168.0.13 up
route add -net 192.168.0.0 netmask 255.255.255.0 ath0
route add default gw 192.168.0.1

At least you can use manual configuration as a work around until release -- hoping it's fixed by release.  This works for me right now, but it's not useful outside of APs you know/own really.

---

