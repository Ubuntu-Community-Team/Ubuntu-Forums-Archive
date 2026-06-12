---
title: "need drivers for what I think is a winmodem"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by khris on 2007-07-23
I really need help on how to get and install drivers for my modem :confused:

---

### Post by oilchangeguy on 2007-07-23
> **khris said:**
> I'm very need help on how to get and install drivers for my modem :confused:

is highspeed available in your area?

---

### Post by Shazaam on 2007-07-23
Go here-- [http://www.linuxant.com/drivers/modemident.php?PHPSESSID=7e17dbe36831ca07733d413740126265](http://www.linuxant.com/drivers/modemident.php?PHPSESSID=7e17dbe36831ca07733d413740126265)
And run their scanmodem software. They have two types of drivers for winmodems, free at 14.40 and full speed for $20.

---

### Post by khris on 2007-07-24
I don't know how to use this.

---

### Post by Paulmd on 2007-07-24
> **khris said:**
> I'm very need help on how to get and install drivers for my modem :confused:


It would help very much if you could provide what identifying information you can on your modem.

Or even if it came pre-installed on a major-brand computer, that can help.

---

### Post by khris on 2007-07-24
I think it is an intel ENF656-GSW-INPR

---

### Post by Paulmd on 2007-07-25
> **khris said:**
> I think it is an intel ENF656-GSW-INPR

It's based on the intel 537ep chipset. It's sold as various other 'off brand' modems. (Apollo, NSpire, and probably a few more)

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1230&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1230&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)


Here's the thing: it's available pre-compiled for RedHat, Suse, and a few others. Not Ubuntu or Debian (ubuntu's base.) There is an UNCOMPILED version. But you'll have to deal with even geekier geeks. I've not dealt with much in the way of compiling stuff under Unix/Linux. You'll have to also deal with others to see if the suse package or redhat package may work. [I know redhat packages can be imported via alien, but am not sure how successful that would be. You'd also need to install alien via synaptec (sp?)]


Here's the other possible bugaboo: Intel did NOT make the modem, only the chipset, for correct functioning, you MIGHT need to track down who actually made the modem. In Windows, which I am much more familiar with, Intel's generic driver usually works fine, but not always.

---

### Post by khris on 2007-07-25
Do you think getting a different, older modem would be less complicated?

---

### Post by ieee488 on 2007-07-25
It is easier if you buy a modem that supported without requiring special drivers.

In my case, I lucked out. I have an 8 year old Dell 4100 Dimension and the modem is an OEM US Robotics PCI modem with TI chipset like this   [http://www.xmodem.org/chipsets/ti/ti_700.html](http://www.xmodem.org/chipsets/ti/ti_700.html)

My suggestion is to look on eBay and look at the photo of the modem itself.

Your other option is to buy an external serial NOT USB modem.


this modem on eBay looks like it has TI chipset
[http://cgi.ebay.com/Internal-56k-Gateway-Modem_W0QQitemZ280135435463QQihZ018QQcategoryZ3693QQrdZ1QQcmdZViewItem#ebayphotohosting](http://cgi.ebay.com/Internal-56k-Gateway-Modem_W0QQitemZ280135435463QQihZ018QQcategoryZ3693QQrdZ1QQcmdZViewItem#ebayphotohosting)

---

### Post by khris on 2007-07-25
does an external modem require special drivers?

---

### Post by Paulmd on 2007-07-25
> **khris said:**
> does an external modem require special drivers?

If it's USB, yes. If it's the old style 9-pin serial, no.

---

### Post by Sepero on 2007-09-17
If your modem is an Intel 537ep, you can download the driver already compiled here:
[http://ubuntuforums.org/showthread.php?t=552090](http://ubuntuforums.org/showthread.php?t=552090)

---

### Post by CaptainInsaneO on 2007-09-17
If you indeed have a Winmodem, Google "linmodem". :)

---

