---
title: "20GB disappeared from my MacBook Pro - Where did they go?"
date: 2011-01-11
forum: Apple Hardware Users
---

### Post by bkbroiler on 2011-01-11
Hi,
  I have a new MacBook Pro 6,1 with 8GB RAM and a 256GB SSD hard drive.  I've decided to triple boot it with OSX, Windows7, and Ubuntu 10.10.  However during my second install I seem to have magically lost about 20GB of space on my hard disk.  That is, the total of the partitions comes to about 235GB  instead of 256GB according to bootcamp.  

  In order to do this I followed the corresponding tutorial, found here:

Specifics for Maverick
[https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick)

General MacBook Pro multi-OS install
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac%20OSX,%20Vista,%20and%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac%20OSX,%20Vista,%20and%20Ubuntu)

This worked fine, except for two minor issues.  First rEFIt was extremely slow to load.  Poking around the internet it seemed this might have something to do with the partition setup, but I couldn't be bothered too much with it.  Second, I realized after the fact that I'd installed the 32bit version of Ubuntu, and therefore, even with the PAE kernel extension could only hope to make use of 4GB of RAM for a single process.  
So I started over with a 64bit copy of Maverick.  Yes I tried just re-installing Ubuntu but that did not work.

The second time around I booted into OSX from the install disk, used disk utility to remove the windows and linux related partitions and then ran bootcamp.  It was at this point that it became clear that there was about 20GB missing from the tally that bootcamp was registering.  I'm curious as to what may have happened?

---

### Post by hawkmage on 2011-01-11
It has to do with the fact that drive manufactures use 1,000,000,000 as 1GB instead of (1024 * 1024 * 1024).  So (256 * 1,000,000,000) / (1,024^3) = 238.4

---

### Post by bkbroiler on 2011-01-11
Nevermind.  The issue was just with bootcamp.  Looking at the system in Ubuntu shows the expected results.

Edit: @Hawkmage thanks for the additional info.

---

