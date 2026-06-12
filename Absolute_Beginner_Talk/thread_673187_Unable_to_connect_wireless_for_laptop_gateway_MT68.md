---
title: "Unable to connect wireless for laptop gateway MT6840"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by willie2008 on 2008-01-20
Hi,

I am having trouble connecting with my wireless.  I have gateway toshiba model MT6840.  I have checked for device recognition and found that the wireless is listed as Intel (R) PRO/Wireless 3945 Network Connection driver for linux it is enabled and status: in use

I have reached the 3rd step in checking which say to use windows driver?  How do I do that and do I need to do it?  It says use NIS..

Thanks,
willie

---

### Post by Speedoo on 2008-01-20
To use a Windows driver, you need ndiswrapper.  Instructions for installation are here:
ndiswrapper.sourceforge.net/
Wish I had an Intel wireless card!  My Gateway MT6459 came with the Realtek rtl8187 which is NOT very Linux friendly!
Good luck,

---

### Post by willie2008 on 2008-01-29
Hi,

Thank you for the response.  But I run into one more obstacle.  I am using windows vista home premium.  I read the doc and it said the drivers are not supported yet.

What else can I do?  (I tried to install windows on my laptop but was unable to because it could not recognise my hard drive)

Thanks,

---

### Post by Speedoo on 2008-01-29
You should download the WinXP driver from here:

[http://www.intel.com/support/wireless/wlan/pro3945abg/index.htm](http://www.intel.com/support/wireless/wlan/pro3945abg/index.htm)

keep track of where you download it, then use that driver when installing ndiswrapper.

---

