---
title: "Ubuntu 10.10 Installer Baulks!"
date: 2010-12-03
forum: Apple Hardware Users
---

### Post by riccardo on 2010-12-03
Having got my installation started by choosing the 'alternate' iso ... I managed to get about 3/4 of the way through the installation and suddenly the installation baulked almost 95% of the way through the install of the 900 plus programs. It flipped me back to the expert menu.  Repeating the step caused the same error.  I had no option but to cancel the install.  

Have others noticed this issue??


Can I get through the installation by disconnecting the eth0 cable ... and completing the install from the cdrom??  I recognise this will leave me a big download to be completed after the install ... but will this avoid whatever is causing this bomb??

Any suggestions??


riccardo

---

### Post by shawnhcorey on 2010-12-03
> **riccardo said:**
> Have others noticed this issue??

Not with the Alternate CD.

> **riccardo said:**
> Can I get through the installation by disconnecting the eth0 cable ... and completing the install from the cdrom??  I recognise this will leave me a big download to be completed after the install ... but will this avoid whatever is causing this bomb??

I don't know if this will help but the installer checks the hardware and downloads any drivers it doesn't already have.  You would have to install the drivers later.


> **riccardo said:**
> Any suggestions??

Use a LiveUSB.  See:
[LIST]
[*][HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")

[*][HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware")
[/LIST]

---

### Post by conal on 2010-12-03
Removing the eth0 cable in is unlikely to make a difference, but no you don't need to be connected at all to do the install. It's just makes things a bit easier as it automatically detects and configures your network connection during the install.  

I have no Idea what went wrong, but if nobody has a better suggestion  I'd say try installing Xubuntu instead, as that has just worked on my G4. You can install the ubuntu-desktop package after the install.

---

### Post by conal on 2010-12-03
Sorry, didn't see your post shawnhcorey. Your answer is better!

---

