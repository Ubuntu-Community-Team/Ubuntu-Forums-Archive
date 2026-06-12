---
title: "Wireless card?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by SteveJ on 2006-12-11
I know that this is a common question. I've tried searching this forum and associated docs - but I simply don't speak Ubuntu well enough (ok, not at all).

I installed Ubuntu into my wifes laptop, and I can't seem to get the wireless connection to work. Under Network Settings, I see a wireless card - I put in the correct Essid and password - but I still can't get on the network. I don't know where to begin troubleshooting it.

Thanks, SteveJ

---

### Post by aysiu on 2006-12-11
I don't know anything about wireless (not having a wireless connection myself), but someone else could probably help you if you post what wireless card you have.

---

### Post by SteveJ on 2006-12-11
Sorry, thanks

It is a Linksys wpc54g

---

### Post by SteveJ on 2006-12-12
OK, 

I managed to find something usefull in this Ubuntu unleashed book:

I did a iwconfig, and on eth1 I get several things:

802.11g zd1211 ESSID:"JFamily"
Mode: Managed Frequency:2.412 GHz Access Point: Invalid
Bit Rate = 1 Mb/s
Encryption key:1122-3344-55 Security mode:open
Link Quality = 64/100 Signal level = 65/100 


Thats not realy my Encrpytion key but I put it in using;
iwconfig eth1 encryption 1122334455


My Router is set to an ESSID of "JFamily", with WEP security, 64bit, 1122334455 for the key.

What should I set my access point and security mode to in iwconfig?



I hate to say it guys - but this is so much easier in Windows.

Thanks

SteveJ

---

