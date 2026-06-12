---
title: "cannot get websites; cannot find usb stick"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by lcv on 2007-12-31
Have just installed ubuntu 7.10 64 onto my machine. AMD64 3000, abit guru mb, netgear WG311T card and d-link dsl-g624t adsl. Two hd - 4gb fat32 and sata 160gb.

loaded to 4gb drive, now dual boots ubuntu/xp.  Good good.  BUT, cannot find usb stick, and although wireless connection seems good (pinged everyone - ok; even traceroute is happy) cannot persuade firefox (2006) to connect to a website.

Should I just load 32bit 7.10 and pray?

Does it support PnP?

I am determined to make it work, my wife is not as enthusiastic!

---

### Post by stijngysemans on 2007-12-31
> **lcv said:**
> I am determined to make it work, my wife is not as enthusiastic!
This is great! 

Are you able to ping outside your LAN? These look like network problems to me. 
Open a terminal and type "ifconfig" to review your current ipaddress. 
Maybe you have to set a proxy?

---

### Post by lcv on 2007-12-31
Yep, BBC website no less. Firefox just times out. I did get onto fsf.org early on but nothing since.

---

### Post by lcv on 2007-12-31
stijngysemans

Thanks for help re network suggestion. Turned off IPv6 and hey presto

I'm getting there

Cheers

---

### Post by bapoumba on 2007-12-31
> **lcv said:**
> cannot find usb stick
What is the output to 
```
lsusb
```
when the stick is plugged in?

---

