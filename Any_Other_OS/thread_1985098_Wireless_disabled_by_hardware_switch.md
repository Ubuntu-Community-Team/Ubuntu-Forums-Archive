---
title: "Wireless disabled by hardware switch"
date: 2012-05-22
forum: Any Other OS
---

### Post by C110mint on 2012-05-22
I have a Acer Travelmate C110 laptop and I put Linux Mint 11 on it but the wireless will not work. I have tried to do the things three people told me to two weeks ago but still no go. Keeps saying Wireless Disabled by Hardward Switch.  Cannot get the wireless to work. the computer works great hard wired into the the router but will not work. Tried sudo rfkill and that does not work.  Anyone have this problem and was able to fix it???

---

### Post by HunterDX77M on 2012-05-22
Sorry for my stupid question, but do you actually have a WiFi switch on your keyboard (on one of the function buttons)? I have the message "wireless disabled by hardware switch" right now in my own network menu, but that is because I disabled it myself with the WiFi button on my keyboard (since I am connected via ethernet to my router at the moment).

Also, do you have another OS on that machine (like Windows)? If so, boot into that and see if wireless is also disabled there (and can be re-enabled).

---

### Post by ts3 on 2012-05-22
> **HunterDX77M said:**
> Sorry for my stupid question, but do you actually have a WiFi switch on your keyboard (on one of the function buttons)?

+1

If you have a hardware switch and simply pressing it does not work I'd suggest running in a terminal

```
sudo rfkill unblock all
```

then toggling the switch and running the same command again.  This works on my hp when the hardware switch starts acting up.

---

