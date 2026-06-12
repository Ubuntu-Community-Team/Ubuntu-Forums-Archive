---
title: "Picking a Wireless Card"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by derouge on 2006-08-14
Hey, I'm about to buy a new wireless card (someone snapped the antenae on the old one) and was curious as to which ones will just work out of the box, or with very minimal configuration? I'd prefer to keep it cheap, $50 is the maximum I'd pay, but I want something reliable. The card I had was a DLink DWL-G520. It worked great. In the Windows system we have a DWL-G520+ which has worked well for the past 2+ years. I'd like something as dependable as these cards.

So, any suggestions?

---

### Post by davebgimp on 2006-08-14
Here's a list of wireless hardware tested on ubuntu:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

The model you're looking at does have some issues but it looks like it is usable, after some work. A quote from the page I linked above concerning your model:

> DAPPER: Nearly works out-of-the-box, but had to add "wireless-rate 11M" to /etc/network/interfaces + reboot or two. BREEZY: Works out of the box with breezy. Works well, even with WEP. (Note: Some G520 may use acx100 instead.) HOARY: Rev. B of this card will not work out-of-the-box with Hoary--the madwifi drivers that shipped with Hoary are too old. An updated linux-restricted-modules* package is available [WWW] [here]("http://ubuntupc.com/ubuntu/public-sources/linux-restricted-modules-2.6.10-5-386_2.6.10.5-1gb_i386.deb") Note that this package is not officially supported. Some users have reported problems with WPA in the forums.

---

