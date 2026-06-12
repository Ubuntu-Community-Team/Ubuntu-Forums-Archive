---
title: "Dual boot MBP5,3 having issues booting 12.04 (w/ pic)"
date: 2012-11-03
forum: Apple Hardware Users
---

### Post by JLen on 2012-11-03
Been looking around, but have not been able to find a fix for this problem, I apologize if I have not looked thoroughly enough (on these forums).

I'm new to anything Linux, so me diving into installing Ubuntu on a Mac is quite strange, to say the least.
Any help that could be thrown at me is highly appreciated. :)

Some background info; I've clean installed my MBP in order to get a nice dual boot of Ubuntu/Mac OS X and to do so I followed this guide: [[COLOR="Blue"]https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Detailed_How-To[/COLOR]]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Detailed_How-To")
I couldn't completely follow the guide, specifically under 'Start Installing' the last step of the installer did not show an Advanced button, to install the boot loader grub.

After that, in rEFIt, it did not let me sync the partition tables as it said they were already synced.
So then I decided to give it a try and selected Ubuntu in rEFIt, which seemed to get me in grub (version 1.99-21ubuntu3.1).
In grub I selected the top/default option *(Ubuntu, with Linux 3.2.0-29-generic-pae)* and it got me the following screen: [[COLOR="Blue"]Image link here[/COLOR]]("http://i.imgur.com/Wbx1L.jpg")
I rebooted and decided to try the recovery mode, which worked fine and it prompted me with a few options, I then chose 'Resume normal boot' which got me straight into the login screen of Ubuntu.

And maybe this was a bad decision, but I've installed software updates within Ubuntu after I did get in.
So the version of grub is now '1.99-21ubuntu**3.4**' and the first option now says 'Ubuntu, with Linux 3.2.0-**32**-generic-pae' (it's still giving me that weird screen).

This is all the information that I can think of right now, I'd greatly appreciate anyone helping me in this matter.

Greets,
JLen

---

