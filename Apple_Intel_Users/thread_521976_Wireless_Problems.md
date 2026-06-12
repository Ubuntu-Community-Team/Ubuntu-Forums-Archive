---
title: "Wireless Problems"
date: 2007-08-10
forum: Apple Intel Users
---

### Post by templets on 2007-08-10
Hi, I can't seem to get my wireless working on my MacBook.  I have Ubuntu 7.04 Feisty Fawn.  All of the other solutions I have seen have not worked becauase most of them require a connection to the internet (my MacBook only has wireless, which isn't working).

Fortunately I have a desktop with Windows which can connect to the internet but Ubuntu seems to be having problems detecting my card.  If necessary I could download files to my flash drive and then transfer them to my MacBook.  When I run lspci in a terminal it says:
     02:00.0 Network controller: Atheros Comunications, Inc. Unknown device 0024 (rev 01)

I guess this means that it doesn't recognize the network card.  I was able to connect to wireless with Mac OS X 10.0.4 but I accidently wiped my drive when installing Ubuntu so I'm stuck with Ubuntu at the moment.  I'm pretty sure I had AirPort Extreme, if that helps.

I tried the "sudo iwlist ath0 scan" but it just says:
    ath0         Interface doesn't support scanning.

Any help would be appreciated, Thanks.

---

### Post by moore.bryan on 2007-08-10
*atheros chipsets are handled by [madwifi]("http://www.madwifi.org/") drivers, so i'd check them out.  [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi")'s a howto which might help out.  i'd also suggest using [wicd]("http://wicd.sourceforge.net/") to handle your wireless networks.*

---

