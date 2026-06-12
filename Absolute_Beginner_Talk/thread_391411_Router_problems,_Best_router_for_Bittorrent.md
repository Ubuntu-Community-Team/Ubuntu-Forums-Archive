---
title: "Router problems, Best router for Bittorrent?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by webjames on 2007-03-23
Hi, i live in a house with 4 people sharing a 10meg VirginMedia interenet connection. everything is working ok. except when i run azureus my internet connection keeps dropping out. on the azureus website it says about many connactions could crash the router, i think this may be the problem. ([http://www.azureuswiki.com/index.php...sual_solutions](http://www.azureuswiki.com/index.php...sual_solutions))

at the moment there is 2 connections wired, and two wireless with mac address security.
as i will be using bit torrent i need a router which will stand up to a lot of connections whilst supporting the other computers also has to have UPnP.

i have a linksys WRT54GC with Firmware Version: v1.03.0

i have heard this is crappy it's a 'compact' router, and i think it's rubbish.

i thought it would be nice to have gigabit connections between the two wired computers, i am thinking of buying something as cheap as i can second hand of eBay, but I'm willing to pay more for more.
anyone had good experiences with any models?

Thank you!

kind regards,
James

---

### Post by Hallvor on 2007-03-23
Before you throw your router away, why not give it a new firmware and install DD-wrt on it? If you are thinking of buying a new one anyway, what is there to lose? I have a Linksys router myself - one of the bad ones with stripped memory that run on WXworks WRT54GS v5. Anyway, they had a guide on [http://www.DD-wrt.com](http://www.DD-wrt.com) that showed me how to install some good (linux-based) firmware. (Linux is also very good in routers!) It works much better now, and it handles heavy bittorrent usage without a problem. It is a good idea to reduce the time of TCP/UDP timeouts in the router settings, or else it may slow down because of too many connections.

---

### Post by Hallvor on 2007-03-23
Anyway, if you need a new one, I`d buy one of these: 

[http://www.dd-wrt.com/shop/catalog/index.php?cPath=21&osCsid=c2d307e97d1c006dd88adb2dc2b6c327](http://www.dd-wrt.com/shop/catalog/index.php?cPath=21&osCsid=c2d307e97d1c006dd88adb2dc2b6c327)

---

### Post by webjames on 2007-03-23
i have looked at several third party Linux firmware projects, none of which has my router listed on its compatibilities list. i have looked at:
OpenWrt
DD-WRT
Sveasoft

shame, are you saying that it may work anyway?
could i break the router trying it out?

thanks
james

---

### Post by webjames on 2007-03-23
thing is it only has 100 connection not 1000, seems DD-WRT is good firmware thats two reccomendations so far. could i put DD-WRT on my router even though it doesn't say it's compatable?
WRT54GC

regards,
James

---

### Post by webjames on 2007-03-23
i have just found this:
[http://forumz.tomshardware.com/network/Difference-routers-compact-regular-ftopict21820.html](http://forumz.tomshardware.com/network/Difference-routers-compact-regular-ftopict21820.html)
unfortunately it says that my router is not compatible.

looks like i shall be buying a new one.

any ideas?

---

### Post by Hallvor on 2007-03-23
Try the forum on DD-wrt before trying to flash it yourself. And if you make a mistake, you may still break your router, even if it is compatible.

The safest thing would be to sell it to someone and order a new one.



Edit: Too slow.

---

### Post by webjames on 2007-03-23
yeah i can't risk not having an internet connection whilst i play around, work is dependant on it.

how about:
[http://cgi.ebay.co.uk/Belkin-125g-Wireless-DSL-Router-4-port-gigabit-switch_W0QQitemZ190093806727QQcategoryZ44997QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/Belkin-125g-Wireless-DSL-Router-4-port-gigabit-switch_W0QQitemZ190093806727QQcategoryZ44997QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

i don't know about belkin. any good? stand up to a lot of connections?

thanks

---

### Post by Hallvor on 2007-03-23
I`d buy a Buffalo or a Linksys with at least 4 mb flash and at least 16 mb ram, and put new firmware on it, or buy one with firmware preinstalled.

Also, take a look at this one: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/642465.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/642465.html)

---

### Post by webjames on 2007-03-23
> **Hallvor said:**
> I`d buy a Buffalo or a Linksys with at least 4 mb flash and at least 16 mb ram, and put new firmware on it, or buy one with firmware preinstalled.

Also, take a look at this one: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/642465.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/642465.html)

i've had a look at that, i don't like the sound of the hard drive of the Asus WL-500g Premium, also the price tag. just want a standard router, this DD-WRT firmware sounds the dogs whatsits 4096 connections sounds plenty!

what about getting a wrt56g standard? and putting the DD-WRT firmware on it? does this have enough memory and ram?

---

### Post by Hallvor on 2007-03-23
Do you mean a WRT54G? In that case, yes. They are inexpensive, and version 1-4 has plenty of flash and ram. The version number is usually printed on the bottom of the router. Just avoid buying the v5 or higher, as it is stripped of flash and ram. You can still run the micro version of dd-wrt on them, and it will work, but not as good.

---

### Post by webjames on 2007-03-23
i've been having a look on the dd-wrt website and have decided on the WRT56GS v1.1:
200mhz
32ram
8flash memory

thanks for the support and I'll post a message when it comes to say how the upgrade and transfer went!

thanks again

regards,
James

PS good info here: [http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices)

---

### Post by Hallvor on 2007-03-23
Wish I had a router like that. :)

You are welcome. Good luck! :)



Hallvor

---

