---
title: "Netgear Wireless PC Card (wg511v2) problems?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Chet Hardin on 2007-07-05
Hey. I have been having trouble with my wifi card for awhile now. After doing some research, I found a guide that helped me mash together a simple system that seems to work perfectly. 

I hope this helps someone else out.

Below is the results of this process.

First, I follow *this* guide (noting the awesome of sudo nautilus and the other super-awesomeness of mv):
[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

Following these instructions works like a charm. 

But this guide is for a Dell and obviously I needed to use a different driver. I have been trying to use the wg511v2 driver that came on the disc with my hardware and it stinks. So I switched to driver mrv8335. I found it here (who knows how long it will be online):

[http://people.freebsd.org/~wpaul/marvell/](http://people.freebsd.org/~wpaul/marvell/)

Now I am online. Easy.

---

### Post by babysteps on 2007-07-29
Thanks for posting.  I've been looking for those drivers. Mine are Netgear Wireless PC card WG511v2_rev 03.  Previously I'd been looking for version 2, but then now I'm realizing that it might actually be a verion 3. My computer identifies it as a Marvell chip 88w8335 (Libertas).  I will try to use that with Dapper 6.06. and see how it goes....

babysteps


> **Chet Hardin said:**
> Hey. I have been having trouble with my wifi card for awhile now. After doing some research, I found a guide that helped me mash together a simple system that seems to work perfectly. 

I hope this helps someone else out.

Below is the results of this process.

First, I follow *this* guide (noting the awesome of sudo nautilus and the other super-awesomeness of mv):
[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

Following these instructions works like a charm. 

But this guide is for a Dell and obviously I needed to use a different driver. I have been trying to use the wg511v2 driver that came on the disc with my hardware and it stinks. So I switched to driver mrv8335. I found it here (who knows how long it will be online):

[http://people.freebsd.org/~wpaul/marvell/](http://people.freebsd.org/~wpaul/marvell/)

Now I am online. Easy.

---

### Post by babysteps on 2007-08-07
> **babysteps said:**
> Thanks for posting.  I've been looking for those drivers. Mine are Netgear Wireless PC card WG511v2_rev 03.  Previously I'd been looking for version 2, but then now I'm realizing that it might actually be a verion 3. My computer identifies it as a Marvell chip 88w8335 (Libertas).  I will try to use that with Dapper 6.06. and see how it goes....

babysteps

Just wanted to say that I got really close with the method and the drivers you linked to using Ubuntu 6.06., Dapper Drake.  Yet, somehow, I couldn't get online, despite all the tweaking in the /etc/network/interfaces.

I downloaded and burned an alternate CD image of Kubuntu 6.06.  I also found on the Ndiswrapper website the list of supported cards and their drivers.  I found that the lspci output of the Netgear WG511v2_rev 03 (made in China) matched that of the ENLWI-G_Driver_Utility_98SE-ME-2000-XP perfectly.  So I downloaded that(use the XP version of the mrv8000c driver), and used the method in Chet Hardin's original post:

 [http://ubuntu1501.blogspot.com/2007/...dell-1501.html](http://ubuntu1501.blogspot.com/2007/...dell-1501.html)

I got to the very same spot where I can scan with wlan0 but cannot associate with anything.  AT this point, before tweaking anything in /etc/network/interfaces, I made sure that wlan0 showed up  in iwconfig.  Then I used the Wireless assistant program in Kubuntu, and thus, for the first time in 4 months was able to get online with my compaq laptop!   Each time I boot up I have to use the wireless assistant to connect, but it's been working nicely. 

Just a few reminders:
1)I used Ndiswrapper 1.47 (which has no preempt) If I remember correctly, the 1.8 wasn't working out for this particular combo.

2) Before issuing the sudo make for Ndiswrapper, blacklist mrv8k in Kubuntu.

Here's the link to Ndiswrapper page for this card look at #24 under letter M:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)
Card: Marvell Technology Group Ltd. 88w8335 Libertas 802.11b/g Wireless (rev 03) [http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=4&pid=15](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=4&pid=15) (product profile)

********************************************************************************************************8********    *
      Chipset: Marvell Technology Group Ltd. 88w8335 Libertas 802.11b/g Wireless (rev 03)
    *
      pciid: 11ab:1faa (rev 03)
    *
      Windows Driver: [http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip](http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip). Used WinXP driver.
    *
      Other: Ndiswrapper 1.34, Recompiled kernel 2.6.18.3, without smp, with kernel debug and without 4kstacks. Debian Testing “Etch”. WPA not tested.

 **************************************************************

---

