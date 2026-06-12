---
title: "Install Ubuntu 14.04 onto a SD Card on a Mac Mini"
date: 2014-07-10
forum: Apple Hardware Users
---

### Post by rramalho on 2014-07-10
Hi!

I've been trying to install Ubuntu 14.04 (amd64+mac) on my late 2012 Mac mini. I've found several articles on the net about the subject, but I can't really get to the point of making the machine recognize the SD card as a boot option.

I tried several partitioning types (MBR and GPT) and none gave me results. The installation runs off the USB stick, and I can install to the SD Card. When the installation finishes, the SD Card doesn't appear as a valid boot option.

Can anyone help me? I'm reading the rEFInd page [http://www.rodsbooks.com/refind/]("http://www.rodsbooks.com/refind/") to try to understand how I can boot the system off the SD Card.

Thank you all!

---

### Post by bapoumba on 2014-07-11
*Thread moved to **Apple Users**.*

---

### Post by wn1ytw on 2015-02-03
According to Apple you can boot to an SD card if the card is formatted properly.

This is from an Apple site:
[COLOR=#333333][FONT=Myriad Set Pro]**Can I install Mac OS X on an SD storage device and use it as a startup volume?**

Yes. Change the default partition table to GUID using Disk Utility, and format the card to use the Mac OS Extended file format to do so.[/FONT][/COLOR]

[http://support.apple.com/en-us/HT3553](http://support.apple.com/en-us/HT3553)

---

