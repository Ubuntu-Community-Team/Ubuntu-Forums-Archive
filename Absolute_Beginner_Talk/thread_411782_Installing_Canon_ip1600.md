---
title: "Installing Canon ip1600"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-04-17
I'm having trouble installing this. It's poorly supported but quite a few people seem to be able to get it working. I've searched a bit on the forum and tried everything I could find. This is what I did:
1. Downloaded the rpms for the ip2200. There aren't any drivers for the ip1600, but this is the one other people have had success with. Apparently it's nearly the same printer.
2. Installed alien, libxml1, libpng3.
3. Coverted the rpms to debs.
4. Intstalled the debs (cnijfilter-common_2.60-2_i386.deb, cnijfilter-ip2200_2.60-2_i386.deb, cnijfilter-ip2200-lprng_2.60-2_i386.deb)
5. Done this: ```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3 
sudo ldconfig

```
Now libtiff.so.4 and libtiff.so.3 both point to libtiff.so.4.2.1. I don't really understand this, but I did it anyway.

5 Restarted cups (rebooted actually, after restarting cups didn't work)

6. Go to system>admin>printers>new printer.
The ip1600 shows up twice, but when I click on either, the new ip2200 drivers don't show up.

So that's where I'm at. Any suggestions?

Thanks

---

### Post by compiledkernel on 2007-04-17
[http://openprinting.org/show_printer.cgi?recnum=Canon-iP1500](http://openprinting.org/show_printer.cgi?recnum=Canon-iP1500)

Shows the iP1500 , the lesser of the models in that range. 

It assumes GutenPrint as its primary driver, have you tried this?

---

### Post by Fidelio on 2007-04-17
I have just tried that, but no joy.
Also when I use the add a printer wizard and get to 'step 2 of 3, printer driver' I get a range of pixma printers in the list (although not the ip1600) but if I try any of them, the 'forward' button is grayed out.

Can anyone tell me why the ip2200 driver isn't showing in the list? If i click on the deb files to try and reinstall it, I get a message saying it's already installed. I'm pretty sure this driver is the way to go.

---

### Post by Fidelio on 2007-04-17
Anyone help with this?
Basically I did this, but with the canon ip2200 drivers [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)
but the ip2200 drivers don't show up as a choice when I go to add a new printer.

I'm not even at the stage of trying to get this driver to work yet.

---

### Post by ramjet_1953 on 2007-04-17
TurboPrint claim to support your printer:

[http://www.turboprint.de/english.ht](http://www.turboprint.de/english.ht)

You can always download the demo, to make sure.

Unfortunately, the registered version isn't free, but it's a whole lot less than buying a new prinnter.

Regards,
Roger :cool:

---

### Post by Fidelio on 2007-04-18
Sorted. The ip2200 drivers work perfectly. I just didn't read the last little bit of the documentation properly. The drivers don't show up in the printer manager until you click on install driver and navigate to  /usr/share/cups/model/canonip2200.ppd.
Some other things. The test page didn't print, so I nearly gave up, but I tried printing from abiword and it worked. Also there are 2 ip1600 printers listed in the print manager, but only one of them (the top one I think) worked for me. Thanks everyone,

---

