---
title: "Problems with Ubuntu"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by researchsci on 2007-02-26
Okay, after getting no help on IRC, I thought I'd come here and try to get some help. Ubuntu installed flawlessly on my laptop, except I cant' get my wifi to work at all. I followed some of the tutorials for the RT61 driver setup, but when I install it, the devices just disappeared out of the networking tab. Does anyone have any suggestions. I would like to stay with Ubuntu, but if I can't get the wifi to work, I don't think that will be possible.

---

### Post by aysiu on 2007-02-26
Was [this thread](http://www.ubuntuforums.org/showthread.php?t=132980) one of the tutorials you followed?

Also, do you have the *network-manager* package installed?

---

### Post by researchsci on 2007-02-26
yes, that would be the. Where do I get the 'network-manager' package at?

---

### Post by aysiu on 2007-02-26
> **researchsci said:**
> yes, that would be the. Where do I get the 'network-manager' package at?
It's going to be tricky without a direct internet connection, but [this post](http://ubuntuforums.org/showthread.php?p=1774934#post1774934) and this website should help you:
[http://packages.ubuntu.com/edgy/net/network-manager](http://packages.ubuntu.com/edgy/net/network-manager)

---

### Post by researchsci on 2007-02-26
Okay, I just plugged in the computer to my ethernet port, and I have internet onmy laptop now, but I installed network-manager, and I can't find it under the applications part of the desktop

---

### Post by researchsci on 2007-02-26
I've got network-manager working now, but my wireless still is awol

---

### Post by researchsci on 2007-02-26
i tried to use ndiswrapper with it, but I assume it's not supported for my card iguess? on network manager I can see my exact info for my wireless card, but other than that it does nothing.

---

### Post by researchsci on 2007-02-26
If anybody could give any other suggestions, it would be greatly appreciated. I don't want to have to reinstall windows, but without wifi my laptop is useless to me.

---

### Post by shane634 on 2007-02-26
Is it a pci or usb card??  Try this in a terminal



 ```
lspci
```

  If is a pci card. Or this 

```
lsusb
``` 

  If it is a usb card. Then we can help you from there.

---

### Post by researchsci on 2007-02-26
It's a pci card.

---

### Post by researchsci on 2007-02-26
this i believe is what you need for my info.

00:0b.0 Network controller: Ralink RT2561/RT61 802.11g PCI
 I also have a pci nic card, but that works great.

---

### Post by researchsci on 2007-02-26
I'd really appreciate any help anyone can give me. This is depressing because if I can't get it working I'll have to reinstall windows : (

---

### Post by rccharles on 2007-02-26
> **researchsci said:**
> I'd really appreciate any help anyone can give me. This is depressing because if I can't get it working I'll have to reinstall windows : (

Try this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

--------

Try a google search on:
Ralink RT2561/RT61 802.11g PCI ubuntu

--------

Did you look into ndswrapper?

--------

I'm not really an expert on WiFi so that is why my hints are kinda cryptic.


Robert

---

### Post by researchsci on 2007-02-27
I tried ndiswrapper, and I had everything in the right directories for an install, and it just laughed at me. I'll try these other fixes this afternoon (have classes all day), and get back on here, and write what has/has not worked.

---

### Post by researchsci on 2007-02-27
Everything worked great (I could even see other wireless networks if I scanned for them) up to this part.

modprobe --remove rt61pci

then it all went to crap for me
any hints? Now I can't even see that I ever had a wireles device on my networking tab.

---

### Post by researchsci on 2007-02-27
PS I tried following the tutorial again, and now when I try to scan it just says that the device doesn't exist at all

---

### Post by researchsci on 2007-02-27
Sorry, I swear I'm not spamming my own post. Also, I read that in dapper that the RT61 works out of the box, is that true? Because if it is... I'm might just downgrade.

---

### Post by researchsci on 2007-02-27
If anyone has ever encountered this problem, I beg you, please tell me how to fix it.

---

### Post by researchsci on 2007-02-28
I reinstalled, tried the method described in the howto, and got the same problems. I attempted another reinstall, tried ndiswrappter again, no avail. This is driving me nuts.

---

### Post by researchsci on 2007-02-28
If someone could plz give me a hand on this, I would greatly appreciate it.

---

### Post by nickoli_02 on 2007-02-28
> **researchsci said:**
> Everything worked great (I could even see other wireless networks if I scanned for them) up to this part.

modprobe --remove rt61pci

then it all went to crap for me
any hints? Now I can't even see that I ever had a wireles device on my networking tab.

You removed the module that controls your wireless card, of course you won't be able to use it now!

If it's true that Dapper supports your card out of the box, it may be worth it to use Dapper instead if it's giving you this much trouble. Personally, I've been much happier with Dapper than I ever was with Edgy. Edgy doesn't like some of my hardware either :(

---

### Post by researchsci on 2007-02-28
If you see the tutorials though, after that I try to enable another module with the nonbroken driver on it. So it should work. I'm installing dapper right now just in case... :)

---

