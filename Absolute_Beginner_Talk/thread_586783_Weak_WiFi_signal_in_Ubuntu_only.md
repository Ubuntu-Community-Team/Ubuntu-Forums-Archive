---
title: "Weak WiFi signal in Ubuntu only"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Shakey_Jake33 on 2007-10-22
Basically I'm using the Gutsy Gibbon LiveCD to see if Ubuntu does all that I need before I ditch Vista.  My main use on this PC is the use of HD video (1080p H.264 and the like).

However, the WiFi signal is real weak in Ubuntu.  I'm about 3 feet from the router, and it's 100% excellent in Vista.  Does anyone know what's causing this?  This would put me off from using it tbh.

Not sure what actual chipset it is, it's the onboard WiFi on the Asus P5W DH Deluxe motherboard.

Thanks!

---

### Post by KCPokes on 2007-10-22
What are you using to tell you the WiFi signal?  I have experienced that not all the utilities represent the signal strength accurately.  In my conky setup my signal will show at 90%, but in Wicd it'll show around 50%.  Not sure why they don't line up, but I tend to believe the info I'm pulling directly, via conky, versus what shows up in Wicd.

---

### Post by Shakey_Jake33 on 2007-10-22
Umm, that little Wifi icon in the top right hand corner :P  I'm new to Ubuntu.  But the net speed is definately slow to a crawl anyway, so I think it's accurate.

---

### Post by KCPokes on 2007-10-22
Wifi is a challenge in linux, in general.  Signal strength is not going to be your only determining factor in speed.  I've had slow speeds, regardless of signal strength, due to driver limitations.  Moving away from the default drivers (in my case they were the rtl8187 drivers) and going the ndiswrapper route has noticeably improved my speeds.

---

### Post by Seisen on 2007-10-22
Its most likely the driver, I had a d-link wifi card that ran unbearably slow in dapper and then I had to use ndiswrapper in edgy. To find out what wireless card put this in the terminal

```
lspci
```

---

### Post by Johnny_Too_Bad on 2007-10-24
I'm also getting a very weak signal strength.  Currently, I am sitting about one foot away from my wireless router and it says I'm only connecting on 50% signal strength.  That can't be right, but I have a feeling it is.

However, weak signal strength is better than no wireless at all, which is what I was going on before Gutsy released.  Hurray for Gutsy!

---

### Post by shae on 2007-10-24
Well it depends on what wireless card you have.  For example madwifi incorrectly reports the signal strength.

---

### Post by sujoy on 2007-10-24
I am using a lenovo laptop with broadcom wireless in it. The restricted driver manager installed the firmware and driver correctly. However, the network manager was hard to use, never showed my wireless or wired connections, just put up a manual configuration banner.

I installed network selector and now it works fine. Oh! by the way, i am at present about 25feets away from the router and my signal strength is 95% :) So I guess its a problem with drivers and firmwares.

---

### Post by Johnny_Too_Bad on 2007-10-24
I guess it's just that Network Manager is incorrect, because no matter where I go in my house, it's always about 50% (or two bars).

---

### Post by Henrywantstobeapenguin on 2008-01-28
I have the same problem :-( can't use wifi in my room as a result, meaning Ubuntu is currently not really worth it for me.

---

