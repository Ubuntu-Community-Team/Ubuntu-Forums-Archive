---
title: "Cannot get ndiswrapper to install, and having difficulty with DWA-642 recognition."
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by SDPrice on 2007-07-11
I am currently running Ubuntu 7.04 "Feisty Fawn" software.  It does not recognize my D-Link Wireless N DWA-642 card.  I have used the help screens to try and get the drivers loaded, but with no success.  

I get a message that tells me ndiswrapper is not installed.  I did have a friend of mine assist me in getting all the updates needed for Ubuntu, which included ndiswrapper.  After this, I went back to the help screens and managed to get to the last few steps.  When I typed sudo depmod –a, it seemed to proceed, but when I proceeded to type in the next command (sudo modprobe ndiswrapper), my computer froze up.

Because my computer kept freezing up, I decided to reload Ubuntu 7.04.  Since then, ndiswrapper does not work.  I have it downloaded to my desktop, but cannot get it installed.

I use my wireless card to connect to the internet, and cannot get it to work properly.  Most fixes I have found require me to be connected to the internet, and I do not have internet at home.  When I attempted to use the MS wireless card I had prior to the DWA-642, Ubuntu recognized the card, but it seemed the card was not turned on because the lights on the card were turned off.

I am new to Ubuntu, and commands used, causing me to become very frustrated with this OS.  If I can just get my wireless card(s) working with this system, I am sure everything else will fall into place.  Help me please.

---

### Post by Espreon on 2007-07-11
Okay...

Completely remove the ndiswrapper stuff (With Synaptic [it is in the system menu])

then:

Search for ndisgtk and install it, then reinstall the other ndiswrapper stuff.

Then Goto System>Administration>Windows Wireless Drivers then hit add then select the .ini or .inf file that is your driver.

If no avail look at the ndiswrapper wiki, google ndiswrapper.

Look for the compatibility page.

I doubt my remedy will work, maybe the current version of Ndiswrapper, the card and the current Ubuntu kernel.
Ndiswrapper does not work for all card ya know....
If all fails I suggest getting a Linux compatible card.

---

