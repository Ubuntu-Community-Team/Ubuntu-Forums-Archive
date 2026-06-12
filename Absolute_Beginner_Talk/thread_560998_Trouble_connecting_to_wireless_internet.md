---
title: "Trouble connecting to wireless internet"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-09-27
I just finished installing Ubuntu and I cant get my internet connection up on my Linksys Wireless-G network adaptor. Ubuntu does detect it and begin to search for available wireless networks, but when I attempt to connect to my own network it asks for my passphrase and I get stuck at that point. I use an ASCII code of 5 sets with decimal pts between each two number set but when I input this, with or without the decimal pts, the connection box greys out and im unable to connect. When I try this as a passphrase through 128-bit encryption it never connects. Any help would be greatly appreciated, since i'd much rather be asking all the important Ubuntu questions through Ubuntu rather than Vista...yuck.

---

### Post by lisati on 2007-09-27
I'm not familiar with the settings that Linksys routers come with out of the box, but it *almost* sounds like you are confusing the WEP or WPA passphrase with an IP address. Have you had any joy with the 64-bit  passphrase?

---

### Post by devosion on 2007-09-27
I tried the 64bit passphrase when I initially installed Ubuntu a few months ago and that didnt work. After doing some digging it looks like im going to have to use ndiswrapper and a linux driver to get it to work....time to have some fun.

---

### Post by Austin_KW on 2007-09-27
WEP uses either 40 or 104 bit encryption keys.
These are sometimes called 64 or 128 bit keys.

The 40(64) bit key is specified by 5 acsii characters or 10 hex digits (0..9,a..f)
The 104(128 ) bit key is specified by 13 acsii characters or 26 hex digits

A passphrase is an easy to remember character string that is used to generate the 10/26 hex digits that is used as the actual key. When you enter the passphrase on the router it should tell you the actual hex KEY it generated. This KEY is probably what you want to set in the wireless adapter configuration.

That said, your should consider using WPA encryption as WEP can be cracked in 2 minutes.

---

