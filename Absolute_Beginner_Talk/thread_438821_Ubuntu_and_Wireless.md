---
title: "Ubuntu and Wireless"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Volvex on 2007-05-10
Looking at the sheer number of them, I'm pretty sure you all groan when you see another wireless thread, but I can't find an answer to my problem anywhere. 

First of all, the card is detected and apparently supported by Ubuntu. My router has no security on it, since I live in a very remote place and don't need to worry about it. So I set my computer thusly, and a check appears next to my wireless connection. But I can't connect. I tried setting a WEP key, but all the same stuff happens.  I've used the same card and wireless settings on another computer with Edgy Eft, and all the setup that was required was turning the computer on. What's so different about it now? 

Also, any help I can get *without* downloading software would be appreciated, as the computer with the problem is a desktop on the other side of the house, and I'd rather not drag it out here--though I will if necessary.

---

### Post by Kobalt on 2007-05-10
When you click on your network icon in the notification area (which is Network-Manager) : do you see your network in the list ? What happens when you click it ?

---

### Post by Volvex on 2007-05-10
Thank you for your reply! When I click the Network-Manager, the only option that appears is Manual Configuration.

---

### Post by Kobalt on 2007-05-10
Can you see your wireless interface in System > Admin. > Networks ?

---

### Post by Volvex on 2007-05-10
Yes, there's a check mark next to it, the essid is set to match my router's SSID, and everything is set for DHCP. I currently have no security enabled on my router, to make this (hopefully) go a little easier.

---

### Post by Kobalt on 2007-05-10
Can you please tell us the output of this (it is your network configuration file) : ```
cat /etc/network/interfaces
```
You should only have the following section uncommented (meaning **any** other text in this file must have a # at the begining of the line) : > auto lo
iface lo inet loopback

---

### Post by apienk01 on 2007-05-10
Also be sure to check if your wireless card supports the channel set up on the AP. Many new access points support channels up to 14, and most wireless cards cannot go higher than 11.

---

### Post by Volvex on 2007-05-10
That was exactly the problem! Commented everything out and I'm posting from the computer now! Thank you so much!

---

### Post by Kobalt on 2007-05-10
> **Volvex said:**
> That was exactly the problem! Commented everything out and I'm posting from the computer now! Thank you so much!
Everything but the "auto lo..." couple of lines I mentioned, right ?
If so then you're good to go :)

---

### Post by Volvex on 2007-05-10
Yep, and everything was working until... 

I reset. Now the computer sees the network, but will not connect, even though other computers in the house can.

---

