---
title: "More wireless connection questions"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-13
Ok, so, if I turn off WEP on my router, and then run 

sudo iwconfig wlan0 essid <myESSID> 

my Belkin N1 wireless adapter's blue light flashes and I can then go into 'Network' and select the Belkin, go in and select <myESSID> with no WEP key, and then (and only then) I can run iwconfig and see that the adapter is properly associated with my essid.

If I enable WEP, that ability is lost, even though I enter the correct WEP key, and even if I take the extra step of running

sudo iwconfig wlan0 key restricted <myWEPKEY>

The above does not help and there is no way I can associate the adapter with the ESSID if I have WEP turned on.

So, there must be someone out there more knowledgeable than I as to what could cause this.

I should also mention that through all of this - even when the adapter is associated and functioning and connecting to the internet, if I look at 'Windows Wireless Drivers', I will see that the proper driver is loaded, but hardware present = no.

So, you would think that the adapter would never work under that condition.

What is supposed to happen is that, when I first install the driver, hardware present should be yes, and I should be able to configure the adapter by going into System, Adminstration, Network, and so forth.

At least I have a work around that should keep me connected during my time without a wired connection, but, I sure would like to figure this out so I can stop thinking about the connection and just concentrate on what I need to accomplish on line.

Tips appreciated.

Thanks.

Caruso

---

### Post by shamreez on 2007-05-25
Why dont you try a fresh install of the ndiswrapper and also try to use a static ip instead of auto...
It is worth a shot as mine got running smoothly once i gave a static ip

Check the below if you want some good steps for proper installation of the ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by carusoswi on 2007-05-25
> **shamreez said:**
> Why dont you try a fresh install of the ndiswrapper and also try to use a static ip instead of auto...
It is worth a shot as mine got running smoothly once i gave a static ip

Check the below if you want some good steps for proper installation of the ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

Thanks for the reply.  I will check out the link you provided.  I did try every variation of setup of which I was aware, static IP, auto-assigned IP, WEP on, WEP off.  Nothing at all worked except for auto IP and WEP off.  Numerous installs, uninstalls, system re-installation, all of that over a two day period - nothing worked except to turn off WEP and allow for auto ip addressing.

Also, as I may have mentioned, if I navigate through System-Administration-Windows Wireless Drivers, my driver shows as installed, but no hardware is present.

I can run iwconfig to configure manually.  Still, on occasion, my adapter will lose its association with the ESSID and I have to open up a terminal and run the iwconfig command that restablishes proper association of my adapter the router through which I am connecting to the 'net.

I remember the first time I was able to get my router to work in Ubuntu.  I had just installed 7.04 from scratch and was in the process of downloading updates, etc.  On a whim, I decided to download NDISWrapper using Automatix.  I practically stumbled through the process of loading my wireless driver, but, to my surprise, it worked perfectly - showed up as present in the Windows Wireless Drivers dialogue box and everything.                                           Whatever it is that I did correctly that one time, I have been unable to replicate after I had to reinstall 7.04 because I had not allowed it enough drive space.

Thanks again for your suggestions.

Caruso

---

