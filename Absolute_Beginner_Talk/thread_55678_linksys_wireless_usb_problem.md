---
title: "linksys wireless usb problem"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by Piney Woods on 2005-08-09
I installed ubuntu on one of my desktop computers awhile back, hoping it would detect my linksys usb wireless card.  It didn't.  I installed it with the knowledge that ubuntu was one of the better linux distros. Is there a way I can get my linksys wireless usb adaptor to work with ubuntu?  I have Mepis installed on a toshiba notebook and it found the internal wifi without any problems.   I thought ubunut would do the same but apparently not.  Any help is appreciated.

PW

---

### Post by Jussi Kukkonen on 2005-08-10
Without more information (like the wireless adapter model) we can't really help.

In general there are two different ways to get wireless adapters working: *wlan-ng* for adapters with the prism2-chip and *ndiswrapper* for everything else. Then again there are special cases...

---

### Post by Piney Woods on 2005-08-10
wusb11v4 is the wireless adapter model.  

PW

---

### Post by Jussi Kukkonen on 2005-08-11
[http://www.linux-wlan.org](http://www.linux-wlan.org) compatibility list shows wusb11 2.5 as a prism2-device, which means that the linux-wlan-ng package would be useful... Unfortunately the manufacturers are quite liberal in using the same product name for very different devices. They don't even mention the chipset on their web pages...

Also unfortunately, many people in ubuntuforums seem to be discontent with these (wusb11) linksys devices...

Anyway, I'd probably try installing linux-wlan-ng. Search the forums first, maybe someone has  already solved this (I only skimmed through the posts).

---

