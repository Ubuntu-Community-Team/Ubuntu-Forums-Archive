---
title: "Are SSID and ESSID the same?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by supazio on 2007-04-14
I'm trying to set up my wireless (Router: WRT54GS, adapter: WMP54GS) and I installed the Windows drivers using ndiswrapper (ndisgk) and it says that the drivers are both correct and the hardware is found. Now I'm just wondering if the problem could be that I'm using the SSID in the ESSID space. I assumed they were the same, but it still isn't working.
EDIT: Xubuntu 6.10 Edgy

---

### Post by Stevo0687 on 2007-04-14
I entered my SSID under the ESSID in 6.06 and it works fine.  I'm guessing that, that is not your problem.  I'm sorry I can't help anymore than that.

---

### Post by phossal on 2007-04-14
You're using what, iwconfig? In that case, they're the same. Are you trying to configure your network using either WEP or WPA? If so, try it without first.

---

### Post by Austin_KW on 2007-04-14
They are the same, eSSID is the SSID for an Access point.

---

### Post by chili555 on 2007-04-14
A common error is for the ESSID to be mis-spelled in iwconfig. Just as we wouldn't confuse a family named Smith with a family named Smythe, Linux will not connect to an access point named linksys if you have told iwconfig that your ESSID is Linksys.

The easiest way to verify what the actual ESSID name is being broacast by your router is with:```
iwlist wlan0 scan
```Substitute your wireless interface for wlan0 here.

---

