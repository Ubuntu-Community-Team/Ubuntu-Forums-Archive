---
title: "Intermitent Wifi on Macbook Pro 7,1 Mid 2010"
date: 2016-12-09
forum: Apple Hardware Users
---

### Post by darkaten1 on 2016-12-09
I recently installed Ubuntu on my Macbook Pro 7,1 Mid 2010. The wifi only works intermittently. The wifi card is a Broadcom BCM 4322 and I have the STA wireless (bcmwl-kernel-source).

lspci:
```
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```

Any ideas to get it working consistently?

Thanks!!!

---

### Post by darkaten1 on 2016-12-09
So, I seem to have gotten it to work consistently now. I've reboot the machine several times and it's picking up my wifi network everytime. After trying several different driver options I went back to the install CD and installed /pool/restricted/b/bcmwl/*.deb.

---

### Post by darkaten1 on 2016-12-11
Apparently that driver did NOT fix the issue. The wifi is still intermittently working. I have tried everything I know to do or read about. At this point I'm able to work with this but it is a bit of a bother.

If anyone has any ideas on how to get the wifi consistently work I would appreciate hearing them. [Here are the options]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") that I have tried.

---

### Post by anandamide on 2016-12-12
I've just installed Ubuntu 16.04 on my Macbook air 2013 and had the same problem - it's a common issue with Ubuntu and broadcom wifi drivers (I speak from bitter experience!).

I'm in no way qualified to give an informed answer but following the steps given here sorted out the problem for me [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers#60395](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers#60395). Crucially the guide suggests (well, tells) you wipe all previously installed broadcom components before trying anything else. Working from a clean slate might be key here if you've been trying lots of different approaches.

Hope this works out for you. Before now I've nearly broken computers at frustration with Ubuntu and Broadcom

---

