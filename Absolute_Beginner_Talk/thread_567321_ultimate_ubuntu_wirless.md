---
title: "ultimate ubuntu wirless"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by cranshinibon on 2007-10-04
Well I made the switch to ubuntu permanently....vista sucks and slax just isn't for me. however, I am still a novice with ubuntu and linux as a whole so I have a few problems I need to get through. 

The distro I chose was Ultimate Ubuntu....just because it's the best all around with features installed that I need. I installed it on my desktop but I realized I wanna play games and wine doesn't seem to cut it and theres no way to get cedega to work for free. (if there is let me know lol) 

The two main problems I'm running into is on my laptop. 

Specs:

AMD Turion (tm) 64 Mobile
Technology ML-32
1.58 GHz, 896 MB of RAM
ATI Radeon XPress 200M Graphics Card

Broadcom 802.11b/g WLAN Wireless Card

I can't get the wireless card to be recognized by the system...through any means...I tried using the driver from the cd and using the Windows Wireless Utility and grabbing the .inf file but that didn't work. When I open up the WiFi Manager it doesn't even show the wireless card being plugged in. 

Here is what I've tried so far.
I've tried manually setting up the wireless...then rebooting (which worked on my desktop with a Netgear) and it didn't work

Now I thought installing Windows XP and dual booting with Ubuntu Ultimate would work better for finding the preinstalled drivers on the XP system....that's not working too well either. 

Can someone give me a few step by step processes on what I should do to get the broadcom wireless card to connect to the internet. (i don't want to switch distros btw)

Also, I am unable to set up the Desktop Effects, can someone tell me what I need to do prior to getting the desktop effects to work?

Thanks in advance...I really love Ubuntu but I wish I was a little better at troubleshooting it.

---

### Post by cranshinibon on 2007-10-04
anyone?

---

### Post by skymera on 2007-10-04
Cedega IS wine!
you can get it free, you have too google.

if you reinstall XP it will overwrite your MBR and you will lose grub, which means reinstalling Grub.

have you enabled the card? in network-manager
if it needs a driver, nDiswrapper may work.

as for desktop effects, Compiz fusion!

o is the Wireless a USB adaptor or PCI?

---

### Post by cranshinibon on 2007-10-04
hmm thats true about cedega....I just dont know how to install directly from a cd with it. 

What is compiz fusion and how do I configure it.

Under network manager..I believe the card isn't being seen. under hardware information a completely different model of broadcom is being seen.

The wireless card is built into my hp computer. (so its PCI)

I'll give ndiswrapper a shot...but in the meantime do you have any other ideas?

---

### Post by cranshinibon on 2007-10-04
OK I am completely lost now....I just installed ndiswrapper but I can't find the program now. 

Also, with compiz fusion I am trying to set up the different effects that I want but still after all is done..I still can't enable the desktop effects.

Can someone please help me with this broadcom problem...i am so lost right now and i am out of ideas

---

### Post by skymera on 2007-10-04
ok ndiswrapper appears undet system>admin>ndiswrapper

compiz=

alt+f2

compiz --replace

---

### Post by cranshinibon on 2007-10-04
ndiswrapper wasn't there....any other ideas?

i want to get this wireless working first and foremost...I just don't understand why it has to be so complicated.

oh and the compiz --replace didn't do anything I stil get the composite device error message

---

### Post by familyjules74123 on 2007-10-04
try to download your wireless card's driver from their website or find a generic copy that matches it, and then look in system>administration>windows wireless drivers and add the driver through that, that is essentially using the ndiswrapper tool. at least this is how I went about it.

---

