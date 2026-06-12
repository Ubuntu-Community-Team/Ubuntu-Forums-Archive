---
title: "Airnet AWU154 USB 802.11g key works with ndiswrapper in Feisty!"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by namely on 2007-09-14
Hi, Everyone,

This is my first post in the Ubuntu Forums, and it's great to be here after over 20 years of OS hassles with certain products whose names I will not mention. :-)

I was skeptical whether my Airnet AWU154 USB wireless adapter would work in Ubuntu with ndiswrapper since Google showed no other successes getting the AWU154 to work in any flavor of GNU/Linux (hi, RMS!)

Since this USB adapter was the only method I had available for connecting my computer to the router down the hall, I used the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The AWU154 is listed in lsusb as ID 0457:0163 Silicon Integrated Systems Corp.

I was frustrated in trying to find the ndis packages until I realized they're not on the 7.04 Live CD, only on the alternate install CD.  (I've never read so many instructions in my life as I have since trying to get Linux up and running, and the hardest thing has been actually paying attention to what they say!)

Following those instructions got me to where the USB adapter would work for a couple of minutes after a system restart, and then stop.  On a hunch, after one of those restarts  I decided to use those couple of minutes to get ndisgtk (graphical install package) from [http://packages.ubuntu.com](http://packages.ubuntu.com).  ndisgtk wouldn't uninstall the driver I had installed the first time, so had to use ndiswrapper -e drivername.inf to remove the flaky installation by hand.  I wound up removing the driver I copied from my Airnet CD and using nsidgtk to install the WinXP driver I found here:

[http://www.airnetusa.com/downloads/driver/DRXP_AWU154.zip](http://www.airnetusa.com/downloads/driver/DRXP_AWU154.zip)

I was amazed that Ubuntu already had a program installed which was able to extract the .INF and .SYS files from the .zip file.

I also noticed that this USB key seems to be sensitive to which USB port it was in - some worked better than others.

I hope this will help someone.  Good luck!

---

### Post by nonewmsgs on 2007-09-15
> **namely said:**
> Hi, Everyone,

This is my first post in the Ubuntu Forums, and it's great to be here after over 20 years of OS hassles with certain products whose names I will not mention. :-)

I was skeptical whether my Airnet AWU154 USB wireless adapter would work in Ubuntu with ndiswrapper since Google showed no other successes getting the AWU154 to work in any flavor of GNU/Linux (hi, RMS!)

Since this USB adapter was the only method I had available for connecting my computer to the router down the hall, I used the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The AWU154 is listed in lsusb as ID 0457:0163 Silicon Integrated Systems Corp.

I was frustrated in trying to find the ndis packages until I realized they're not on the 7.04 Live CD, only on the alternate install CD...

that's weird.  why would some drivers be on the alt cd instead of the livecd?  and any more software esp the infamous wireless is good progress for not just ubuntu but all linuxes.

and welcome!  the fact that you can follow those directions means that your temporment is probably ideal for linux.

---

