---
title: "Direct Rendering???"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by shane634 on 2006-02-13
How do I turn on direct rendering??  82810 CGC [Chipset Graphics Controller] (rev 03)
 Direct rendering is off. Is there a driver I need to install? This is an onboard card and I have no idea what to do. 

 On a side note everything except this is working quite well. Long time Windows user, and have had very few issues with Ubuntu over the last month. My first comp was a TRS-80 so I am very familiar with the command line lol. Any help is appreciated. Thanks Shane

---

### Post by poofyhairguy on 2006-02-14
[QUOTE=shane634]How do I turn on direct rendering??  82810 CGC [Chipset Graphics Controller] (rev 03)
 Direct rendering is off. Is there a driver I need to install? This is an onboard card and I have no idea what to do. 

 On a side note everything except this is working quite well. Long time Windows user, and have had very few issues with Ubuntu over the last month. My first comp was a TRS-80 so I am very familiar with the command line lol. Any help is appreciated. Thanks Shane[/QUOTE]

I will help you. Graphics is my thing. It seems the card's driver lacks the feature:

[http://support.intel.com/support/graphics/intel810/sb/cs-009125.htm](http://support.intel.com/support/graphics/intel810/sb/cs-009125.htm)

But lets try anyway. This page seems to give an alternative plan to try:

[http://www.jensflorian.com/linux/notebook/](http://www.jensflorian.com/linux/notebook/)

f your manufacturer has one available - get a BIOS update that allows you either to select the memory used for graphics or at least provides 8mb of video memory. Luckily ASUS provides a BIOS Update on the FTP Server to solve this problem. The drawback however is that you need some working copy of Windoze or MSDOS to flash the BIOS. I used the PHLASH Utlity and it worked fine, I now have enough video memory to run the i810 driver with 1024x786 at 32bpp.
 In the character devices submenu enable APGART support, then activate the AGP support for the GLX module and onboard support for the i830 chipset. Do not forget the DRI support and the i830m DRM driver.
<*> /dev/agpgart (AGP Support)
[*] Intel I810/I815/I830M (on-board) support
[*] Intel 440LX/BX/GX and I815/I820/I830M/I830MP/I840/I845/I850/I86
[*] Direct Rendering Manager (XFree86 DRI support)
--- DRM 4.1 drivers
<*>   Intel 830M

---

