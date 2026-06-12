---
title: "Can't access Airport"
date: 2005-12-03
forum: Apple PPC Users
---

### Post by gazman on 2005-12-03
Hi have just installed 5.04 'Hoary Hedgehog' (I've ordered the 5.1 'Breezy Badger' CD but it hasn't arrived yet) onto a G3 iMac with the old Airport card (i.e. non-extreme).

During installation the installer correctly determines that my main ethernet device is my wireless 'Airport' card.  It asks for my WEP key, but then keeps giving me 'Network configuration failed' messages.  I have tried all the options from full autoconfig to full manual install and get the same error message each time.

The rest of the installation went well, but once logged in I cannot access the Airport.  From the Network Monitor tool I keep getting 0% signal strength.  I have made it the default interface.  Deactivated then reactivated, reset all the information, restarted.  None of this made any difference so I tried re-installing.  Same results.  I am writing this from the same G3 iMac whilst booted to OSX and connected to the net via the Airport so I know its not a hardware issue.  I also know all the settings are correct because I set up the Airport network (a G4 iMac and Pismo PowerBook also connected through OSX).

Any help or advice?

---

### Post by gazman on 2005-12-04
OK, have now got this working - I'm writing this in Ubuntu - but can't find any way to connect or disconnect the Airport from dialling into the internet.

[edit: i.e. have to connect and disconnect from one of the other macs running OSX]

---

### Post by gazman on 2005-12-08
[QUOTE=gazman]OK, have now got this working - I'm writing this in Ubuntu - but can't find any way to connect or disconnect the Airport from dialling into the internet.

[edit: i.e. have to connect and disconnect from one of the other macs running OSX][/QUOTE]

Finally solved this by installing [AirportStatus]("http://www.kristian-m.de/projects/AirportStatus/"), which was a PITA to configure (like I've everything else I've tried to configure on Ubuntu so far) but is now installed and working fine.

BTW, thanks for all the help and support shown to a brand new Ubuntu user!:???:

---

### Post by king_arthur on 2005-12-13
[quote=gazman]Hi have just installed 5.04 'Hoary Hedgehog' (I've ordered the 5.1 'Breezy Badger' CD but it hasn't arrived yet) onto a G3 iMac with the old Airport card (i.e. non-extreme).

During installation the installer correctly determines that my main ethernet device is my wireless 'Airport' card.  It asks for my WEP key, but then keeps giving me 'Network configuration failed' messages.  I have tried all the options from full autoconfig to full manual install and get the same error message each time.

The rest of the installation went well, but once logged in I cannot access the Airport.  From the Network Monitor tool I keep getting 0% signal strength.  I have made it the default interface.  Deactivated then reactivated, reset all the information, restarted.  None of this made any difference so I tried re-installing.  Same results.  I am writing this from the same G3 iMac whilst booted to OSX and connected to the net via the Airport so I know its not a hardware issue.  I also know all the settings are correct because I set up the Airport network (a G4 iMac and Pismo PowerBook also connected through OSX).

Any help or advice?[/quote] 
Hi there, I have exactly the same problem: 
installation went on smootly and after everything was finished, no Airport connection available.
I can see two NIC interfaces (eth0 and eth1) in the network control panel.
eht0 works fine and is from where I am posting this one, Airport is apparently being confused with an additional NIC and doesn't work.
The iwconfig command does not show any information, airport insmod doesn't work, why???

Also my OSX volumes are not being recognized.
Very frustrating, it all worked so well with the live CD...

Could you please shed some light and tell me how you did it?

Thanks

/Pieter

---

