---
title: "Palm Sync w/ Evolution"
date: 2004-11-14
forum: Apple PPC Users
---

### Post by Down8ve on 2004-11-14
Like many of you I have failed to get my Visor to sync with Evolution.

When I go through the Gnome-Pilot setup it asks which connection I use.  After looking in my /dev folder I see no dev/usb listing, so I tried the /dev/ttyS0 and /dev/ttyS1 connections both as "Serial" and "USB" in the setup dialogues.  No luck.

The manual says to give my user account read/write permissions to these devices, yet I see they have group read/write permissions anyway.  What am I missing?

FYI, I have synced this device on OSX, so I suppose when this works I should select "Yes, I've used sync software with this device before" in the pilot dialogue.

Thanks,

Scott

---

### Post by ChrisQ on 2004-11-15
I had problems as well. The uber hack that fixed it was to set the device to ttyUSB2, try and sync, have it time out, then try and sync again and ttyUSB2 and 3 would be used and that would work. I've had problems with syncing in suse too, so I don't think it's a ubuntu thing.

---

### Post by rkn on 2004-11-15
[QUOTE=Down8ve]Like many of you I have failed to get my Visor to sync with Evolution.

When I go through the Gnome-Pilot setup it asks which connection I use.  After looking in my /dev folder I see no dev/usb listing, so I tried the /dev/ttyS0 and /dev/ttyS1 connections both as "Serial" and "USB" in the setup dialogues.  No luck. [/quote]

Try using /dev/ttyUSB1

(the device actually uses ttyUSB0 & ttyUSB1)
I use [ Jpilot ](http://jpilot.org/) .  Ubuntu worked for my Zire 31.  All I had to do was put /dev/ttyUSB1 in my sync preferences and everything worked!

> 
The manual says to give my user account read/write permissions to these devices, yet I see they have group read/write permissions anyway.  What am I missing?

Make sure that the user is a member of the group.
> 
FYI, I have synced this device on OSX, so I suppose when this works I should select "Yes, I've used sync software with this device before" in the pilot dialogue.

Thanks,

Scott

---

### Post by Down8ve on 2004-11-20
[QUOTE=rkn]Try using /dev/ttyUSB1

(the device actually uses ttyUSB0 & ttyUSB1)
I use [ Jpilot ](http://jpilot.org/) .  Ubuntu worked for my Zire 31.  All I had to do was put /dev/ttyUSB1 in my sync preferences and everything worked!


Make sure that the user is a member of the group.[/QUOTE]
 The dev/ttyUSB1 change got communication going, but the ID number is screwy.  At the initial setup it returned a negitive number, -1233586777.  In the looking around I have done the "-" seems to be a bad thing.

I sync this device on Mac OSX, so am not thrilled with resetting the device and losing data.

Scott

---

