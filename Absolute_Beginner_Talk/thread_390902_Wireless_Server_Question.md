---
title: "Wireless Server Question"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by yagiska on 2007-03-22
Let me start by apologizing for not posting this in the wireless section, but this was the only place I was able to find a "new thread" button.

Here's my scenario:

At the center of my home network is a WRT54G running DD-WRT firmware. I've got the wireless portion of my network secured with WPA2 using AES. I use MAC address filtering and static IP addresses for all clients on my network.

I have an over-built server running Edgy, whose primary function is file serving, with a secondary function of running any other server tasks my various interests may require. To file serve, I am using NFS. I have denied all hosts except the client IPs on my network (using ALL as the daemon in both hosts.deny and hosts.allow). I allow mounting of the home directory (to allow for private network directories) and mounting of a common folder (for shared network directories). The server is connected via ethernet.

The clients on my network consist of 2 laptops, a Nintendo Wii, and a Nintendo DS. One laptop is running Edgy, the other Windows XP (soon to switch). The DS is the newest addition. Everything works very well and I am fairly confident in my security (as an aside, let me know if I shouldn't be). The only problem is the DS.

As is well lamented on the net, the DS only supports WEP. Downgrading my network to WEP is just not an option, for obvious reasons. 

What I would like to do is install a wireless card on the server, and allow the server to act as an AP for legacy clients (those only supporting WEP) such as the DS. However, I need a solution that won't downgrade the security on the rest of my network. Therefore, I need to be able to allow internet access, but isolate the WEP clients from the router, WPA clients, and server. 

I believe I can isolate the server by only allowing whatever daemon will give WEP clients internet access, and denying all other daemons to the WEP clients. Then, even if my WEP is cracked and one of my devices' MACs spoofed, the only access gained would be to the internet.

Of course, I have no idea what to use to allow the wireless NIC to function as an AP, how to give WEP clients accessing the AP access to the internet, or how to isolate them from the router.

Please, any help would be greatly appreciated.

Thanks,
Kristopher

---

### Post by carlosfocker on 2007-03-22
You may want to check out the Nintendo Wi-Fi USB Connector. It allows you to create a AP for your DS to connect to with out having to downgrade your network.

[http://store.nintendo.com/webapp/wcs/stores/servlet/ProductDisplay?lastAction=setCurr&jspStoreDir=NOASTORE&languageId=-1&catalogId=null&categoryId=11157&productId=95704&currency=USD&storeId=10001&ddkey=SetCurrencyPreference](http://store.nintendo.com/webapp/wcs/stores/servlet/ProductDisplay?lastAction=setCurr&jspStoreDir=NOASTORE&languageId=-1&catalogId=null&categoryId=11157&productId=95704&currency=USD&storeId=10001&ddkey=SetCurrencyPreference)

OR third party Universal WiFi Link for Sony PSP and Nintendo DS Lite

[http://www.ddrgame.com/game-accessory-wifi-link.html](http://www.ddrgame.com/game-accessory-wifi-link.html)

These are only offically supported for Windows but I read some where that the first one uses a Ralink chipset which is supported by Ubuntu. I'm gonna search around a little more but I figured I'd make you aware

---

### Post by yagiska on 2007-03-28
Just to close out, I've found a solution.

I happened to have another WRT54G lying around, so I set it up behind my main router and am only using MAC filtering to block unwanted clients. It is completely isolated from my normal network, so even if someone spoofs my MAC, the best they can do surf the net.

---

