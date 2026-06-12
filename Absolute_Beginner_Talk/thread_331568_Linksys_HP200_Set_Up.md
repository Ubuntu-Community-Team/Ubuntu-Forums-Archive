---
title: "Linksys HP200 Set Up"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Morningstar on 2007-01-04
I thought I'd make a quick post outlining how I set up ubuntu 6.06 with the Linksys HP200 and a Dell Inspiron 8100 in case it can help anyone else. This is my first experience with any form of linux.

The Dell Inspiron is a 1.3 ghz with 256mb of ram and a 48gb hard drive.

I installed Ubuntu 6.06 directly over the top of Windows XP formatting the whole disc and letting Ubuntu partition the drive. On the install the card was recognised as being there but was disabled. 

I first installed *ndiswrapper-utils_1.8-0ubuntu2_i386.deb* followed by *ndisgtk_0.6-0ubuntu1_all.deb* 

I then copied the .sys, .info and .bin files from the HP200 drivers disc to a new file in my home directory, the files I copied across are* LSMVNDS.inf, FwRAD16.bin, FwRAD17.bin, Lstinds4.sys,  MRV8335.sys, MRV8335NT.sys, MRV8335XP.sys, tnet1130.sys and tnet1130x.sys*. There are two other .info files but they are for other cards.

Using *system / administration / window wireless drivers* I installed the drivers and the card was recognised.

A restart saw the card powered up and recognised as Wlan0 in, *system / administration / networking* I used the SSID and WEP key from my wireless access point and left it set to DHCP. It took two attempts for the card to find the router and then everything connected.

Now I just have to learn about the rest of Ubuntu / Linux. I hope this is of help to someone else

---

