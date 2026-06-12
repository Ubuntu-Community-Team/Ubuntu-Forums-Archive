---
title: "Trouble with using Netgear WG111T Adapter in Feisty Fawn"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by R-ch4rd on 2007-10-13
Hi, I'm completely new to Linux, but not to computers. I have a WG111T adapter, and I can't connect to the Internet on Feisty Fawn (I'm typing this on my Windows Laptop). Since I can't connect to the internet, there is no way of me downloading Ndiswrapper to my Ubuntu Computer. I DO have a flash drive if needed. I tried to download the latest stable version of Ndiswrapper onto my flash drive and copy it onto my Linux computer, but the Linux Computer would not recognize anything that I typed into the terminal relating to Ndiswrapper, and when I rebooted, the folder containing Ndiswrapper on my desktop had disappeared. Any help would be greatly appreciated. Thanks in advance :)

~R-ch4rd

---

### Post by vgrisham on 2007-10-14
Is this a wireless card or an ethernet card? What chipset is running it? 

Before you spend a lot of time and energy trying to get the card to work in Feisty, you might want [download]("http://releases.ubuntu.com/releases/7.10/") the Release Candidate of 7.10 (Gutsy Gibbon). Boot to the live CD and see if Gutsy picks up your card. Gutsy seems to be a major step forward as far as hardware support goes. Everything in my box was detected and configured automatically, and that is a first for my hardware.

Good luck.

---

### Post by R-ch4rd on 2007-10-15
I believe it is a wireless card with an atheros chipset. It connects via USB. Here's the website: [http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG111T.aspx](http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG111T.aspx) 

Thanks for the response. :)

---

### Post by R-ch4rd on 2007-10-15
Also, I was thinking about waiting 3 days before the stable version of Gutsy comes out. I'm not a great beta tester. :(

---

### Post by vgrisham on 2007-10-15
> **R-ch4rd said:**
> Also, I was thinking about waiting 3 days before the stable version of Gutsy comes out. I'm not a great beta tester. :(

I wasn't suggesting that you install Gutsy--just that you boot into the live cd which will not affect your current system at all. That way you can see if the hardware problem has been resolved in the upcoming version. Many other hardware issues seem to have been resolved in 7.10. 

And you're very welcome regarding your thanks for the response; I am no Ubuntu expert. I installed Dapper a year ago, and a whole lot of people on this forum stepped up to help me with my learning curve. I try to do the same. 

Incidentally, I too had an atheros based wireless nic. It worked swell and without any configuration in Dapper, then would not work in Edgy or Feisty. I finally gave up and bought a [buffalo ethernet adapter]("http://www.buffalotech.com/products/wireless/wireless-g-mimo-performance/wireless-g-mimo-performance-ethernet-converter/"), which externalized my wireless configuration. 

Good luck, and please update this thread with your progress in case somebody else out there has the same problem.

---

### Post by R-ch4rd on 2007-10-18
Sorry for the delayed response. :( Anyway, I have gotten Gutsy on a live CD and booted from it, yet it has still not been able to detect my Netgear WG111T wireless USB dongle. Any further suggestions would be appreciated. :)

---

### Post by vgrisham on 2007-10-18
> **R-ch4rd said:**
> Sorry for the delayed response. :( Anyway, I have gotten Gutsy on a live CD and booted from it, yet it has still not been able to detect my Netgear WG111T wireless USB dongle. Any further suggestions would be appreciated. :)

Well, dang, the easiest solution didn't work. 

Okay, here's the next thing I would try. Go to System>Administration>Restricted Drivers. If there is anything listed related to your Atheros card, enable it. 

If there isn't, then this thread seems to have some info that might help:  [http://ubuntuforums.org/showthread.php?t=258732&page=2](http://ubuntuforums.org/showthread.php?t=258732&page=2)

---

