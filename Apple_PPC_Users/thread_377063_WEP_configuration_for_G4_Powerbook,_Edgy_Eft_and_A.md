---
title: "WEP configuration for G4 Powerbook, Edgy Eft and Airport (snow) base station"
date: 2007-03-05
forum: Apple PPC Users
---

### Post by Maxwell Rocatanski on 2007-03-05
Edgy Eft works great on my 15" Titanium G4 Powerbook.  My only complaint is that it won't negotiate a WEP password with my older Apple Airport (snow--i.e. non-extreme) basestation.  If I leave the basestation unsecured, I can get an IP address without issue.  If I enable WEP on the basestation, nothing seems to allow authentication.  I've tried all the different settings (ASCII, Hex) and resetting the password at the hub, but it just doesn't seem to know how to deal with a WEP security password (as opposed to a WPA, which isn't an option on this base station).  I've installed wifi-radar to help with some of the configuration management, but again, nothing I've tried seems to work.

Please help!  I live next to a park and several apartment buildings, so I'd really rather not leave my network open to the world.

Thanks,

Maxwell:confused:

---

### Post by Maxwell Rocatanski on 2007-03-06
Well folks, since nobody was able to answer my questions, I did some further forum surfing and Googling and found this useful link:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Basically it's a "how to" to get WPA encryption to work with Ubuntu using Network Manager.  I didn't need the wpasupplicant component, so it was mostly a matter of installing the network manager (gnome) and selecting the security authentication being used by my wireless access point.  I'm not sure why the System>Administration>Network Tools wouldn't let me configure for an ASCII WEP open network setup, but I believe I tried every possible permutation with that tool before moving on to wifi-radar (which also didn't work) and then finally stumbling upon the apparent solution with Network Manager.

Suffice it to say that it's working now and I'm not going to question why (after poking at this thing for a day and a half).  I just hope any other Mac PPC users out there struggling with a WEP configuration over an older Apple Airport network (i.e. non-Extreme) find this useful.

The details of my system are: Dual boot setup Edgy Eft/Mac OS X.4.8, 15" Titanium G4 Powerbook (DVI) with original Apple internal Airport card.  My wireless hub is an Apple Snow Airport base station.

Good Luck!

Maxwell

---

