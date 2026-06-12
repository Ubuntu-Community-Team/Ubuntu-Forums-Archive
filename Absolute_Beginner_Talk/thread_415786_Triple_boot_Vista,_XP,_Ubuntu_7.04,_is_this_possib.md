---
title: "Triple boot: Vista, XP, Ubuntu 7.04, is this possible? Also a wireless question."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Zorko on 2007-04-20
After running a VERY old machine with ubuntu I have decided I like the OS so much it needs to be installed on my main PC. My main PC runs Vista, and XP, and dual boots using Vista's boot menu thing. Now as I understand it when I install ubuntu it will overwrite that booter. This leads to my question: What will happen? Will Vista be detected along side my XP install, and all be in one menu, this is what I hope. Will XP and Vista show up as one item, and selecting that item take me to vistas boot loader? If so I can deal with this.

However, I have been told this might not happen, and that Ubuntu's boot loader will detect XP, but miss Vista. If this happens, is there a way to make either of other two possibilities occur?

Also, I plan on buying another hard drive, specifically for Ubuntu. Does ubuntu deal well with Nforce SATA controllers, or would it be best for me to get another IDE drive?

I also plan on buying [THIS](http://www.aria.co.uk/Products/Peripherals/Network+Products/Adapter/Wireless-G+(54Mbps)/+Linksys+Wmp55ag+Dual+Band?productId=22078)
as it contains the Atheros chipset according to [THIS](http://users.linpro.no/janl/hardware/wifi.html) list, which I have heard is the easiest to work with under Ubuntu.  Does this mean it will work "out of the box" in Ubuntu? Does MadWifi support WPA or will I have to change my router back to WEP?
(I should note that my PC runs Ubuntu fine off a liveCD, but picks up no network with my current card, which uses a Texas Instruments chip)

Sorry for the large amount of questions, but I really like the look of ubuntu, and want to try it with the least amount of apprehension.

---

### Post by lingnoi on 2007-04-21
I do not know exactly what you mean but I have installed Ubuntu on my SATA drive and I have an nForce 4 motherboard.

I hope that answers at least part of your question.

---

### Post by BuckoA51 on 2007-04-21
I've been trying to get XP Vista and Ubuntu all on one computer for the past 2 days now. The closest I got was using the utility Bootit NG ([http://www.terabyteunlimited.com/](http://www.terabyteunlimited.com/)) However I don't think it works properly with Linux as when I try to boot my Linux partition it says it is not bootable. 

As a work around, I can go into my BIOS and change the boot priority so that the Ubutu drive boots first, then Ubutu boots no problem, but its a bit of a poor workaround.

---

### Post by markyb73 on 2007-04-21
Hi!

1st post been registered for a while :neutral:
Hope my info might help.

I have vista,xp,and feisty all installed on 1 drive in different partitions.
I installed xp first, then vista to a new partiion and on boot the vista bootloader comes up and i can select xp from there "Older Windows or something like that"
Then when i installed ubuntu to some new partitions the grub bootloader got installed and there is a Vista/Longhorn entry which takes me back to the Vista botloader when i can select either windows.
I am sure grub can be edited so all 3 os's show but i haven't got round to having a go at that yet.

Hope this helps :)

---

### Post by jhpope on 2007-04-23
try this

[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

---

