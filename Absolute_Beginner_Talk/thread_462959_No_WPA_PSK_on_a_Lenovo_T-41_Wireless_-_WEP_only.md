---
title: "No WPA PSK on a Lenovo T-41 Wireless - WEP only"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by mollywolly on 2007-06-03
I just switched to Ubuntu Feisty Fawn (and burned the boats - e. g. nuked windows,etc and reformatted the hard drive completely). My wireless connection sees my network but won't let me set up a WPA PSK connection.  It seems to say that only WEP is all that is available. The message says that the device won't support anything but WEP. The hardware device worked with WPA PSK and windows so it doesn't seem to be a hardware problem. 

The wireless device is a Cisco Aironet Wireless 802.11b from AIRONET Wireless Communications.  Any advice would be appreciated.  

I am a beginner, so my ability to answer questions or respond may be slow while I attempt to research the issue...Thanks

---

### Post by wjp.reg on 2007-06-03
if you do a forum search on "supplicant" or "wpa" you will find howtos..

---

### Post by Inxsible on 2007-06-03
Check if this helps

[WPA]("http://ubuntuforums.org/showthread.php?t=263136")

---

### Post by iqag1060 on 2007-06-04
The Cisco airo driver does not support WPA. See the [faq:]("http://www.cisco.com/en/US/products/hw/wireless/ps458/products_qanda_item09186a008019bd57.shtml#may1")
> Q. Does the Linux driver for the Cisco Aironet 350 Series Wireless Card support Wi-Fi Protected Access (WPA) encryption?

    A. No, the Linux drivers for the Cisco Aironet 350 Series Wireless Card do not support WPA. 

There is an open source alternative driver which has been under development for a few years: [https://gna.org/projects/airo-wpa/](https://gna.org/projects/airo-wpa/)

Following the general WPA tutorials will leave you bashing your head against the wall. It should work with WEP and unsecured networks out of the box.

---

