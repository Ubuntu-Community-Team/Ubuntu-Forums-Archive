---
title: "Looking for new sound card"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by oldnumber11 on 2006-05-26
I am giving up on trying to bring my old OSS sound card to life. I will try to get another sound card, My question: Where do I look to find what sound cards are appropriate for my computer? I have Version 5.10. I have a pentium III, 450 MHz, Is this the correct link: [http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix")

Thanks,

---

### Post by Sutekh on 2006-05-26
Yes this is probably the best place to start.  You want to make sure the chipset is supported by ALSA to get the best from your sound card.

Bear in mind that the ALSA cound card matrix might show support for card using the latest ALSA release (1.0.11).  Breezy usees ALSA 1.0.9, and Dapper 1.0.10.  This could make all the difference to your sound.   Of course you can always install the needed ALSA drivers, if things don't work.

For example my Creative SB Live 24bit (uses the ca0106 ALSA driver) did not have 5.1 sound in Breezy (with the 1.0.9), but works great with the Dapper (1.0.10) driver.  


So you should also check out the Ubuntu Wiki for more info on supported cards and which distributions they work best in.  Unfortunately its not very extensive.

[Ubuntu Wiki - Supported Sound Cards]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards")

You should also try seraching the forum to find out what cards *not* to get, by going on the cards that people often have problems with.

---

