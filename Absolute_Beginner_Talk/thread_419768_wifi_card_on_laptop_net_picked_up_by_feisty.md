---
title: "wifi card on laptop net picked up by feisty"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by hatchetman82 on 2007-04-23
Hello.

ive installed 7.04 on a compaq presario 2700 laptop, and it picked up everything but the wireless card.
the card (identified as "wireless PC Card model 0110") is a pcmcia wireless 802.11g adapter.

at first i though this could be solved with ndiswrapper, so i installed it, used ndiswrapper -i to install the driver and verified that ndiswrapper was loaded (modprobe ndiswrapper, then dmesg) -it was.
ndiswrapper -l would display the driver as installed successfully but would not show the "device installed" line they have in their wiki under installation instructions.

the problems doesnt seem to be with ndiswrapper : lspci does not pick up the card. neither does lspci -v.
the only listing that shows the card is lshw, which makes me think the problem goes beyond ndiswrapper.

i have no idea how to continue from here. any help would be appreciated (i'd add command line dumps if i knew what would be helpful)

---

### Post by ghostboy on 2007-05-15
> **hatchetman82 said:**
> Hello.

ive installed 7.04 on a compaq presario 2700 laptop, and it picked up everything but the wireless card.
the card (identified as "wireless PC Card model 0110") is a pcmcia wireless 802.11g adapter.

at first i though this could be solved with ndiswrapper, so i installed it, used ndiswrapper -i to install the driver and verified that ndiswrapper was loaded (modprobe ndiswrapper, then dmesg) -it was.
ndiswrapper -l would display the driver as installed successfully but would not show the "device installed" line they have in their wiki under installation instructions.

the problems doesnt seem to be with ndiswrapper : lspci does not pick up the card. neither does lspci -v.
the only listing that shows the card is lshw, which makes me think the problem goes beyond ndiswrapper.

i have no idea how to continue from here. any help would be appreciated (i'd add command line dumps if i knew what would be helpful)


Check this link out [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108), check it and make sure that your card is supported.  If it is supported, search the forums and see if you can get an answer or see if someone else has developed a work around for this card.

---

### Post by macron1 on 2007-05-15
i had similar problems on a compaq v6000 trying to get wireless going with the ndiswrapper. had some luck tho with bcm43xx-fwcutter following this tutorial [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

Wireless now works, albeit slowly. let us know how you get on tho, i would be interested in attempting ndiswrapper again if i could get a bit of extra speed.

---

