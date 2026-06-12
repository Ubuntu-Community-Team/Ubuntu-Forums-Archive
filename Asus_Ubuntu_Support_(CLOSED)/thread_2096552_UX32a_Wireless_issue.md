---
title: "UX32a Wireless issue"
date: 2012-12-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by crazyrobban on 2012-12-20
I recently installed Ubuntu 12.10 on my Asus Zenbook (UX32a core i3 variant) and everything seems to be working out of the box. Except for my wireless.

I've checked Enable Wireless but it still states that it's disabled. 
I've pressed the physical button to enable it, and bluetooth enables, but still no wifi.

I tried nm-tool and this is what I get:

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        C4:85:08:17:7B: D1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

Any help?  :(

---

### Post by Somewhat Newbie on 2012-12-20
Go the Asus Website always for drivers and see if they have the wireless drivers, download and install, I've found that sometimes Linux will not provide just the right one for all computers, this is best done under the original windows, may also try the extra drivers from Ubuntu that you must install from the repository. hope it helps...

---

### Post by Pjotr123 on 2012-12-20
No driver issue. This might help to switch it on:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on)

---

### Post by crazyrobban on 2012-12-20
> **Pjotr123 said:**
> No driver issue. This might help to switch it on:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on)

Nice! I'll try this tomorrow, left the zenbook at work. Thanks!

---

