---
title: "Using /etc/ekpdrc to get my Epson RX580 printer going"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-02
I'm working with the ekpd settings to get my RX580 going. and I've set the new settings as follows:

PrinterName = lite
PrinterDevicePath = /dev/usblp0
DummyDevicePath = /var/run/ekplp0
CommandServerPort = 35586

But I have no way to save the settings. If I press enter and leave the screen, when I come back, the printer  device path gets reverted back to: /dev/usb/lpo . But from following other posts where they succeeded with this, the path should be /dev/usblpo (no second slash should be there).

How do I "save" these file settings? Also,....of equal concern really, is that I'm supposed to run this command to  create the right PPD file to get the printer listed:

/usr/local/EPAva/LITE/pipslite-install   

But when I run it, I get back "No file or directory found"


I would really appreciate any help on this; I feel like I might be really close to getting this resolved, but one never knows either.

Thanks, Frank B.

---

