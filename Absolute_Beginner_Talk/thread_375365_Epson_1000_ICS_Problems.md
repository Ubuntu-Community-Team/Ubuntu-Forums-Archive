---
title: "Epson 1000 ICS Problems"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-03-03
Hello, i was wondering how to install the Epson 1000  ICS.id the add printer and they did not have my driver so i selected a random one. i tried this a few times and still nothing. i was wondering if anyone could help me?  Also it's a scanner/printer/coppier if that helps. thanks

---

### Post by ewq30131 on 2007-07-06
Installing Epson 1000 ICS on xUbuntu

Hardware:
Averatec 3150H notebook computer
RAM expanded to 640 mb
Epson 1000 ICS Printer attached via USB port

Linux Distribution:
XUbuntu 7.04 &#8220;Feisty&#8221;

Some where on the internet I saw where the driver for &#8220;Espon Stylus Color 777&#8221; could serve as a alternative driver for &#8220;Epson 1000 ICS&#8221;.

I tried using Xubuntu Xcfe desktop menus:
Applications ->  Settings -> Printing
&#8220;New Printer&#8221;
Printer Name: &#8220;Epson06&#8221; [arbitrarily chosen by me]
Select Connection Device &#8220;EPSON 1000 ICS USB #1&#8221;
Printer make: &#8220;Epson&#8221;
Model: &#8220;Stylus Color 777&#8221; [as alternative printer driver]
Driver: &#8220;gutenprint (recommended&#8221;
Click on &#8220;Apply&#8221;

After several seconds got this message:
&#8220;Database Error.  You will need to install the 'gutenprint-foomatic' package in order to use this driver&#8221;

I was tried several ways to install the gutenprint-foomatic package using Synaptic Package Manager, etc. but was not successful.

Note to Xubuntu maintainers:
Please fix it so this will work or at least suggest some viable alternative or work around.

Thanks.

---

### Post by ewq30131 on 2007-07-06
Success!

I opened the Firefox browser.
Typed in the URL &#8220;localhost:631&#8221;
which launched a CUPS web-page (or something like a web-page).

Clicked on the &#8220;Add Printer&#8221; button.
Used
Name: &#8220;Epson08&#8221; [arbitrarily chosen by me]
Device: &#8220;EPSON 1000 ICS USB#1 (EPSON 1000 ICS)&#8221;
Model: &#8220;Epson Stylus Color 777 &#8211; CUPS + Gutenprint v5.0.0.99.1&#8221; [since I had read that Espon Stylus Color 777 driver could be used for Epson 1000 ICS]

And the printer worked thereafter.

What a rush!

---

