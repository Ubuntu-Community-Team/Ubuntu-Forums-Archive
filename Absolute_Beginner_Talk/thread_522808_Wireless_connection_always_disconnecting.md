---
title: "Wireless connection always disconnecting"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-11
hi all! i have a problem with my wireless, everytime i'm connected after awhile it'll just disconnect and i would have to either refresh my wireless connection or disable and then enable my connection again.
I can see that others are not having the same problem so i figure maybe it's because of my laptop or something
I dont see any error message so i cant post anything to show you guys

---

### Post by ugm6hr on 2007-08-11
Perhaps tell us what software you use to connect (?Network Manager), what encryption you use, and what chipset you have:
```
lspci -nn | grep Network
lspci -nn | grep Ethernet
```

If you have Intel or Atheros with Network Manager and WPA - it might just be that combination - it is a known issue.

---

### Post by kinngg on 2007-08-11
whats a WPA? and i think iam using a intel proset wireless

---

### Post by neoguy2012 on 2007-08-11
> **kinngg said:**
> whats a WPA? and i think iam using a intel proset wireless

WPA (Wi-Fi Protected Access)is just a type of encryption (see [http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)).  Unfortunately, I can't help you anymore than that since I have a broadcom card.  :-#

---

### Post by ugm6hr on 2007-08-11
> **kinngg said:**
> whats a WPA? and i think iam using a intel proset wireless

Type the commands above into Terminal (see my signature for "Code entries" if this doesn't make sense), and tell us the results.

Also do this (when wifi is working):
```
iwlist scan
```
And tell us the results - and tell us which ESSID (access point) refers to your router.

WPA is a type of wifi encryption protocol... Whoever set up your wifi network will know what encryption (if any) they used.

---

### Post by akshayas1986 on 2007-09-30
Hey
Well I seem to have a similar problem. I have a Hawking HWU54G USB Wifi Adapter. It keeps dropping the connection every 5 minutes. I thought this was a problem with Ubuntu. But I have the same problem in Windows too. When I checked the reviews for the adapter, most of them have stated that the card BY ITSELF keeps dropping connection. Its a card firmware problem.

So I dont think its because of your OS or driver. Once the card/adapter works for even a couple of minutes, I think the drivers are fine. The problem must be with your adapter/card.

Hope this is of some help to you.

---

