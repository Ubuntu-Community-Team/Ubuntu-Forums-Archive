---
title: "How to connect WiFi Printer"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by pepe0818 on 2007-08-09
How do I connect to a HP PSC 1610 (using driver for PSC 1600, which should work) using an Apple Airport Express? The printer is connected to the Airport and works on both Mac OS X and Windows but I don't know how to set it up, or even it will work, on Ubuntu 7.04

---

### Post by pepe0818 on 2007-08-09
Never mind, I got it working using cups.

---

### Post by JEBB on 2007-08-23
Is there a published procedure using CUPS?  My computer with Ubuntu 7.0.4 doesn't recognize the printer or maybe the path to it.  What name did you put for the printer?

I have a Canon BJC 2100 attached to an AEBS.  I works fine with my Mac and Windows machines.

---

### Post by dwhitney67 on 2007-08-23
Select **System -> Administration -> Printing**.  Wait patiently for the UI to load.

Then select **Network Printer**, and then from the pull-down menu select "TCP Socket, HP JetDirect, Raw connection".

Then enter the IP address (or alias if it is listed in the /etc/hosts file) into the "Host:" field.  Then click on **Forward**.

Next step is to select the appropriate printer you have and then click on **Forward**.

Then enter the printer's biography... Description and Location... whatever, you choose.

Finally click on **Apply**.

This should create an icon on the Printers UI.  Right click on the icon to examine (and set if necessary) any special properties you may need.

P.S.  If this setup does not work for you, then accept my apologies.  It works for my printer that I have networked using an Iogear thingy and with a LaserPrinter at my office.

---

### Post by albertlash on 2008-01-29
Works for me on Gutsy Gibbons, 7.10, with an old school Airport Express (UFO Style) and Samsung 1740. Thanks!!

---

### Post by valmorel on 2008-06-03
Ping dwhitney67
Just a short note of thanks to dwhitney67 for the help on setting up a wifi printer. I have a generic desktop circa 2001 on which I have installed Ubuntu 8.04. I have it running on my home network, which is wifi and includes two Windows machines. My printer is a Canon Pixma ip 4200 which is converted to wifi using a Belkin All-in-One wireless G print server dongle, but had been having trouble making it work. Following the simple instructions you posted, it was a snap. Thanks very very much.
It wont work when one of the Windows machines is connected to it, which is a bit of a pity, but no big problem. Brilliant :-).

---

