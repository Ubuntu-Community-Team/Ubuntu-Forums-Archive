---
title: "Broadcom 4401 on Gutsy Gibbon"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by matchu on 2008-04-17
Mmkay, here's the thing.

Just started with the magical Ubuntu-ness, dual-boot w/ Vista and all that good stuff. Everything's working fine, except that about every single method I've tried for setting up my Broadcom card didn't seem to work out in the end.

For reference, lspci returned:
```
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

So... is there any hope for me? Lemme know if there's some special method I haven't quite discovered yet :)

I think I'll go ahead and uninstall all those random repositories I downloaded so that y'all can help me start from scratch xP

---

### Post by nicedude on 2008-04-19
I will try to point you where you need to be looking. First off If you are trying to setup a Wireless network card I don't think thats it, I believe thats your wired lan interface. To figure out whats happening you should run the following commands to see what network adapters your system is seeing.

ifconfig    <- this will show you all your interfaces

iwconfig   <- this will tell you which ones are wireless

If I am right about what's not working then you have wired access but no wifi - if thats true you need to find out what manufacturer and model # for your wifi chipset and post it here so I & others will have the info needed to figure your problem out. You could also spell out exactly what PC your using such as Laptop or desktop, manufacturer of PC , Model # of PC. All that info will let someone be able to help you to resolve your issues.

---

