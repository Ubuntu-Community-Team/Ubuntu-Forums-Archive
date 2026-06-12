---
title: "New Install on a IBM 600e (2645-4AU)"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by shredd on 2007-11-06
Hi all,

First I'm new to the Linux world - Did allot of reading and it appears that Ubuntu is the route I want to try. 

I have an IBM 600E laptop (2645-4AU) and I have downloaded Ubuntu 7.10 (ISO) - burnt it to a CD.

First thing I have noticed is a error that pops up upon first booting the CD - ACPI : Bios age (1999) fails cutoff (2000) - then it just continues onto the Ubunto load screen. - does not stop - just states this - not sure if this is anything to worry about. 

Second: I have done some reading and I have turned off the quick boot as per most peoples recommendations. But the start of this install to get to the screen that shows the icon of the HD that says "install", takes about 30 minutes to do. Yes I know this is a slower laptop with 198megs of RAM - but I have read that it should still work. This laptop does not have a DVD drive only a CD drive. (Desktop Edition  Ubuntu 7.10 - Supported to 2009)

So now I'm stumped - I get to the screen with the example icon and the install icon and then the HD just churns and churns and does not stop.

Does anyone have any recommendations - thoughts - etc...

TYIA,

---

### Post by hkramski on 2007-11-09
Hi Shredd,

6 weeks ago I did a successful install of Feisty (7.04, Xubuntu Live CD) on a similiar 600E (2645-8A0) without any (serious) problems. Later I upgraded to Gutsy (7.10) - again some strange effects (mwavem/modem still not working, r8180 wlan driver crash) but no real show stoppers.

Some things you may want to try:
[LIST]
[*]Look for the latest BIOS update (INET36WW (= 1.16), 11/20/99) at [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=DSHY-46HLKQ](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=DSHY-46HLKQ) (this was for MY model - double check if it is appropriate for yours!) You may have to make a bootable CD-ROM with a diskette image of this (using VMware/Nero for example) as there is no diskette drive on the 600E.
[*]Follow the directions at [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_600E](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_600E) (pay special attention to the boot parameters "acpi=off pci=noacpi pnpbios=off vga=0x317)
[*]Be sure to unmount any existing windows volumes manually before starting the installer, otherwise the partition step fails - at least the manual one I was using.
[/LIST]

This should get you to a working Feisty installation. I upgraded to Gutsy online using synaptic.

HTH, regards,
   Heinz

---

