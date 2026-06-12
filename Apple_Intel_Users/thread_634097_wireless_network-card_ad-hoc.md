---
title: "wireless network-card ad-hoc"
date: 2007-12-07
forum: Apple Intel Users
---

### Post by omax on 2007-12-07
Hi guys, as far as I understand, Ad-hoc or Monitor mode is not supported by the network-card in my Macbook C2D?

Or is it? Is there anyway to get it running?

```
n1mda@royal:~$ sudo iwconfig ath0 mode ad-hoc essid test
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
n1mda@royal:~$ 

```

Kisses

---

### Post by omax on 2007-12-07
I actually got this working with help from benanzo, that I randomly met on IRC!

Kudos to him, you're great, thanks alot :)

First of all, remove ath_pci module

modprobe -r ath_pci

now reinsert it without creating wifi0

modprobe ath_pci autocreate=none

now use madwifi-tools, if you havn't got it installed, install it

wlanconfig ath create wlandev wifi0 wlanmode adhoc

iwconfig ath1 mode ad-hoc

iwconfig ath1 essid "lol"

ifup ath1

Ad-hoc networking should be up and running :)

---

