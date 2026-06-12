---
title: "having problems setting up network printer"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by bluepowder7 on 2007-12-03
ok, i now actually have TWO problems in setting up a network printer (new HP OfficeJet Pro L7580).

first problem is that the printer icon on the toolbar is now GONE.  i mistakenly pressed "Hide" when it showed up, and now i can't find any way to get it back.  how do i get it to come back?  when it was there, it was telling me that my printer isn't connected (which is the second problem)

second problem is that the printer doesn't appear to "be connected" even after i go through a CUPS setup as well as the Ubuntu -> System -> Admin -> Printers setup screens.  i'm fairly sure i'm following the instructions, but after setting the IP address and loading the PPD file, i try to print a test page - which never ever prints because the "printer is busy" or "is not connected" (depending on who you ask).  of course it is NOT busy cuz i'm the only one here and i just set it up mere moments ago, so i'd know if it's actually busy doing something other than idling...

it's hooked up as a network printer to my router, and i've set a reasonable IP address on the printer itself (i can even ping it and as long as i do "ping -c 4 192.168.1.102" the ping results are fine - if i skip the "-c 4" limit, it pings forever and ever, non stop, well over 300 lines of pinging)

any ideas on what i need to look for or how to "fix" the installation which apparently went bad?

---

### Post by bluepowder7 on 2007-12-03
4 hours later, after a 61 minute call to HP, going through tutorials, and then blindly just saying "screw it, let's try THIS", it works.  completely against the CUPS tutorial, logic, and anything else.

if anyone is searching for how to install an HP OfficeJet Pro L7580 / L7680 / L7780, here's what i did:

* system - admin - printing
* new printer
* AppSocket / HP JetDirect
* hostname is the IP address of the printer (good to use a static IP), just type it in like 192.168.1.102 or whatever it happens to be
* port number 9100 seems to work (default)
* i had the PPD file downloaded from OpenPrinting.org, but you can likely select your printer from the list
* enter some names / labels for it, doesn't seem to matter (first line is how it'll show up from an application, so maybe call it HP_OfficeJet or HP_Photosmart or HP_6180 or whatever)
* print a test page and finally be done with the damned thing


only 4 hours ago i was ready to reach for a beer and a sledgehammer...

---

### Post by samuraiCat on 2007-12-04
> **bluepowder7 said:**
> 4 hours later, after a 61 minute call to HP, going through tutorials, and then blindly just saying "screw it, let's try THIS", it works.  completely against the CUPS tutorial, logic, and anything else.

if anyone is searching for how to install an HP OfficeJet Pro L7580 / L7680 / L7780, here's what i did:

* system - admin - printing
* new printer
* AppSocket / HP JetDirect
* hostname is the IP address of the printer (good to use a static IP), just type it in like 192.168.1.102 or whatever it happens to be
* port number 9100 seems to work (default)
* i had the PPD file downloaded from OpenPrinting.org, but you can likely select your printer from the list
* enter some names / labels for it, doesn't seem to matter (first line is how it'll show up from an application, so maybe call it HP_OfficeJet or HP_Photosmart or HP_6180 or whatever)
* print a test page and finally be done with the damned thing


only 4 hours ago i was ready to reach for a beer and a sledgehammer...

Neat! I'm going to try to set up my HP 5160 on my wireless router tonight. Thanks!

By the way, how did you find out the IP of your printer? I know I could find this out elsewhere, but hey, since I'm here...

---

### Post by bluepowder7 on 2007-12-04
> **samuraiCat said:**
> Neat! I'm going to try to set up my HP 5160 on my wireless router tonight. Thanks!

By the way, how did you find out the IP of your printer? I know I could find this out elsewhere, but hey, since I'm here...

on my machine (Pro L7580), i can set the IP using the printer's own front panel (which, annoyingly, doesn't register until i connect it to the router - so setting IP and then printing network settings gave me 0.0.0.0 all the time until i actually connected it to the router).  i don't know if the other models let you do that from the front panel, or if you need to connect first via USB to set it up, or if you need to install HP's bloatware to get at it.  see if there's a menu item that lets you print current network settings from the printer itself.

---

