---
title: "Help with net connection"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by kristalsoldier on 2007-02-21
Hi...

I am really a newcomer to Ubuntu/ Linux. Actually, though I have been using computers for a while (windows only), aside from point, click and type, I have no idea how the stuff works, which is one (but not the only) of the reason I am looking at Linux. All this just to reiterate that I am a n00b!

Ok. So, I downloaded the 6.06 LTS as a LiveCD and with trepidation ran it on my machine via the dvd drive. Two things caught my attention.

(1) while loading it first said RAID monitoring not detected
(2) 'RNG' not detected.

I know what RAID means (googled it!), but I don't know what the implications of its not being detected means. Also, I have no idea what RNG means and the implications of its non-detection.
 
Well, Ubuntu loads up just fine - mouse works, sound works, display is fantastic. But no net connection. I go to Network Admin. BTW, I have a wireless connection via a Linksys box to the net on XP (preinstalled on the vaio). It recognizes my inbuilt wireless. Asks for the network name - should I be inputting the same info as in XP mode? Then it asks for Ket Type. I have no idea what this is. Then it asks for the WEP key. In XP mode I seem to have 4 sets of 10-digit numbers under the WEP key info. Then it asks for DHCP or Static IP Add. What do I pick? And more importantly (since I want to learn), why? Then it asks for IP Add. Where do I get this from? Subnet Mask...ditto and the same goes for Gateway address.

My objective is once I feel confident in thisnew environment, I'd like to install Ubuntu on my machine with XP. I believe there is a tool in the last stages of development that will allow for reading and writing to NTFS filesystems.

I do apologize for what may seem to be really basic questions, but I did say right at the outset that I am really a newcomer.

In case I have left out any essential info, please do let me know and I will do my best to post the same here.

Many thanks.

---

### Post by Shatrat on 2007-02-21
If you dont have a RAID dont worry about it not being detected, RNG is random number generator, same situation I believe.

DHCP is dynamic host configuration protocol, it gets and configures your IP address, Subnet mask, and Gateway automatically.  Most routers support this so use DHCP unless there is a problem, then you could try Static.

Reading from NTFS is pretty easy, writing is somewhat experimental.  NTFS is undocumented and there are several versions of it, so there isnt really a way to create a driver to write to it 100% reliably when there is no specification for how the filesystem works in the first place.

---

### Post by kristalsoldier on 2007-02-21
> **Shatrat said:**
> If you dont have a RAID dont worry about it not being detected, RNG is random number generator, same situation I believe.

DHCP is dynamic host configuration protocol, it gets and configures your IP address, Subnet mask, and Gateway automatically.  Most routers support this so use DHCP unless there is a problem, then you could try Static.

Reading from NTFS is pretty easy, writing is somewhat experimental.  NTFS is undocumented and there are several versions of it, so there isnt really a way to create a driver to write to it 100% reliably when there is no specification for how the filesystem works in the first place.
 
Thanks. But what do I do about...

Key Type
WEP Ket (in XP mode I seem to have 4 sets of 10-digit numbers)
 
Thanks!

---

### Post by kristalsoldier on 2007-02-21
It worked!!

Am on the net and with Ubuntu!!!!

This is great!!!!!!

Now, I'm gonna play around and explore the possibility of installing this OS in the very near future!

Thanks for helping me out!

---

