---
title: "Help With Printer Setup"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by jcparker500 on 2008-01-30
Hello from a Linux newbie!  I'm pretty efficient around computers (I'm a systems analyst by trade) but all of my experience is in the Windows environment.  I decided to make the leap to Linux on my laptop and I really love Ubuntu so far.

So, I have a small home network,  Windows Vista PC is sharing an HP Color Laserjet 2600n.  Last night I booted from the Ubuntu 7.10 CD on my laptop to make sure it was compatible with all of my hardware - it was.  Using the System - Administration - Printing option I clicked on New Printer and then selected "Windows Printer via SAMBA" and then clicked on the Browse button.  It immediately found the PC the printer is attached to, and the printer itself.  I installed it and printed out several pages.  It was all point and click and so simple.

This morning, I actually installed Ubuntu onto my laptop.  Now, following the exact same process as outlined above, it does not see my printer.  It sees the PC that the printer is attached to, but not the printer.  I checked on the PC to make sure the printer was still shared (it is) and that I can print to it from the PC (I can).  I rebooted the PC and the printer just in case.   I can even browse to shared directories on the Vista box from my laptop, but Ubuntu will not see that shared printer - when it worked so effortlessly last night while I was running off of the CD.  This one really has me baffled.  Any help will be greatly appreciated!

---

### Post by dcstar on 2008-01-30
> **jcparker500 said:**
> Hello from a Linux newbie!  I'm pretty efficient around computers (I'm a systems analyst by trade) but all of my experience is in the Windows environment.  I decided to make the leap to Linux on my laptop and I really love Ubuntu so far.

So, I have a small home network,  Windows Vista PC is sharing an HP Color Laserjet 2600n.  Last night I booted from the Ubuntu 7.10 CD on my laptop to make sure it was compatible with all of my hardware - it was.  Using the System - Administration - Printing option I clicked on New Printer and then selected "Windows Printer via SAMBA" and then clicked on the Browse button.  It immediately found the PC the printer is attached to, and the printer itself.  I installed it and printed out several pages.  It was all point and click and so simple.

This morning, I actually installed Ubuntu onto my laptop.  Now, following the exact same process as outlined above, it does not see my printer.  It sees the PC that the printer is attached to, but not the printer.  I checked on the PC to make sure the printer was still shared (it is) and that I can print to it from the PC (I can).  I rebooted the PC and the printer just in case.   I can even browse to shared directories on the Vista box from my laptop, but Ubuntu will not see that shared printer - when it worked so effortlessly last night while I was running off of the CD.  This one really has me baffled.  Any help will be greatly appreciated!

When you initially connect to a Samba share the resources may not be visible until there is a "Broadcast" notifying other network resources of what is there (which usually occurs at set intervals) - you may have to just wait a while so the Ubuntu PC picks up the respective data from your network.

You can also try to manually "Reload" in Places-Network.

---

### Post by stchman on 2008-01-30
> **jcparker500 said:**
> Hello from a Linux newbie!  I'm pretty efficient around computers (I'm a systems analyst by trade) but all of my experience is in the Windows environment.  I decided to make the leap to Linux on my laptop and I really love Ubuntu so far.

So, I have a small home network,  Windows Vista PC is sharing an HP Color Laserjet 2600n.  Last night I booted from the Ubuntu 7.10 CD on my laptop to make sure it was compatible with all of my hardware - it was.  Using the System - Administration - Printing option I clicked on New Printer and then selected "Windows Printer via SAMBA" and then clicked on the Browse button.  It immediately found the PC the printer is attached to, and the printer itself.  I installed it and printed out several pages.  It was all point and click and so simple.

This morning, I actually installed Ubuntu onto my laptop.  Now, following the exact same process as outlined above, it does not see my printer.  It sees the PC that the printer is attached to, but not the printer.  I checked on the PC to make sure the printer was still shared (it is) and that I can print to it from the PC (I can).  I rebooted the PC and the printer just in case.   I can even browse to shared directories on the Vista box from my laptop, but Ubuntu will not see that shared printer - when it worked so effortlessly last night while I was running off of the CD.  This one really has me baffled.  Any help will be greatly appreciated!

You don't need Samba or anything like that with that particular printer.  The 2600n (n stnds for Network) has a built in print server so just hook it up to your router, assign it an IP address to it outside the DHCP range of your router, and you are good to go.  Hooking up a network printer via USB is a waste.  You paid for the print server so use it.  Gutsy will auto scan your LAN and find the printer.

That is a Zenographics based printer so you will need to use my foo2zjs driver for Gutsy.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Please read the tutorial thoroughly.

---

### Post by jcparker500 on 2008-01-30
I tried the reload, dcstar, but that didn't work either.  Thanks for the tip though!

stchman, I didn't have it hooked up to my router simply because it was too far away from it and it was just simpler plugging a USB cable into my computer (it sits right next to it).  However, I took your advice and dug up a long enough CAT5 out of the garage and have it networked now.

It still bothers me that SAMBA worked when I was running off of the CD, but it won't work off of my installed version.   However I am able to print over the network with no problem so this particular issue is resolved.   Thanks.

Hey, I noticed your World Series avatar.  Watch out for the Tigers this year my friend!  ;-)

---

### Post by stchman on 2008-01-31
> **jcparker500 said:**
> I tried the reload, dcstar, but that didn't work either.  Thanks for the tip though!

stchman, I didn't have it hooked up to my router simply because it was too far away from it and it was just simpler plugging a USB cable into my computer (it sits right next to it).  However, I took your advice and dug up a long enough CAT5 out of the garage and have it networked now.

It still bothers me that SAMBA worked when I was running off of the CD, but it won't work off of my installed version.   However I am able to print over the network with no problem so this particular issue is resolved.   Thanks.

Hey, I noticed your World Series avatar.  Watch out for the Tigers this year my friend!  ;-)

The major drawback on the USB hookup is the PC that the printer is hooked up to MUST be left on for that printer to work.  This way any PC can use the printer as long as the printer is hooked up.

As far as my Cardinals they are going to need some pitching and the Mets are about to pick up Santana so the NL should belong to the Mets.

---

