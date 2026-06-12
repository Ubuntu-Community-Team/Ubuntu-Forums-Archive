---
title: "Installing ADM8211 drivers for Belkin F5D6001 PCI WiFi card"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by lkvee on 2006-03-13
I have a Belkin F5D6001 PCI 802.11b card which I'd still like to use instead of an Ethernet card attached to a router to get WiFi access.

I was successful with using ndiswrapper for this card, but ubuntu only detected the net8180 wrapper and not the hardware itself.

I've read that the ADM8211 drivers featured here [http://aluminum.sourmilk.net/adm8211/](http://aluminum.sourmilk.net/adm8211/) will help ubuntu recognize that Belkin card.

I downloaded the 2.6.15 update and tried to run the make install command.   All I got was an error message about a missing separator.

What did I overlook or neglect when I attempted to install the ADM8211 drivers?

Thanks for reading!

---

### Post by chuckyp on 2006-03-13
Install the drivers from the ndiswrapper wiki list.

---

### Post by lkvee on 2006-03-13
I went here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

I skipped Compile and Install because I thought obtaining ndiswrapper from Synaptic was sufficient.   I headed for the Install Windows Driver steps:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B) and found the Belkin F5D6001 card driver.   

I entered the "(sudo) ndiswrapper -l" command. Terminal should have printed "net8180 driver present, hardware present", but it only printed "net8180 driver present".   There's nothing about hardware.

What did I miss?

---

### Post by lkvee on 2006-03-13
Perhaps I should have gone through the Complie and Install section under:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Thoughts?

---

