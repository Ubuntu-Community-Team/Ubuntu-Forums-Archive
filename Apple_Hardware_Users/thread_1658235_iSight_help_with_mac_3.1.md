---
title: "iSight help with mac 3.1"
date: 2011-01-02
forum: Apple Hardware Users
---

### Post by ruddyrum on 2011-01-02
ok, I have done so much reading on this, but nothing seems to work - I could really use a hand!

I have a macbook (3.1) and have just installed ubuntu 10.10 (no mac partition)

I installed the isight util/tools and have found two different AppleUSBVideoSupport files but neither seem to work.

I copy the AppleUSBVideoSupport file to /lib/firmware then run:

```
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully

```then rebooted the macbook, and still nothing!

The other AppleUSBVideoSupport file does the same, but says its OS X 5 Driver

No cams detected in skype or cheese! Any help is very much appreciated!

Edit: when i installed isight utils, i was presented with an installer. I cant seem to find it again... would like to try and install via that again (although it shouldnt make a difference)

---

### Post by ruddyrum on 2011-01-02
Well, have been trying for hours, still no luck.

Can someone perhaps send me a file which is confirmed working with macbook 3.1?

I have a feeling that the ones i have tried are for newer models

---

