---
title: "UPS / computer shutdown question"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-05-11
If I am running my computer which is connected to a "**BELKINS**" UPS via usb port does the attached screenshot of the "**Power Management Preferences**" mean that my machine will do a graceful system shutdown if I lose A/C power to the wall socket or if I as an experiment unplug the Belkins UPS from the wall socket ?

I other words, does the Ubuntu **Edgy** O/S have automatic system shutdown software built into it ?

Thanks.

---

### Post by Skrynesaver on 2007-05-11
If you unplug your UPS do you get warning messages on the desktop?
If so the signals are being handled correctly and should work.
For more advanced configuration take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=365357")

---

### Post by wpshooter on 2007-05-11
I notice that the thread you reference has all kind of mentions of **APC**upsd.

My UPS is a Belkins brand UPS.

Will the information given in the thread work with a Belkins UPS ?

Thanks.

---

### Post by Skrynesaver on 2007-05-11
I used to have a Belkin way back when, the folks working on the "powerd" project were looking at reverse engineering the protocol Belkin use.  When I upped the number of machines on my network I needed a bigger UPS and after my previous experience I opted for an APC supply.  Apparently Belkin ship a (possibly buggy) closed driver called Buldog with Linux support.  This should be on the drivers CD that came with the UPS.

---

