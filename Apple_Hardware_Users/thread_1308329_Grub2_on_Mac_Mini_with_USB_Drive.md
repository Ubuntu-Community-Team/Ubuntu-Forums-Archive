---
title: "Grub2 on Mac Mini with USB Drive?"
date: 2009-10-31
forum: Apple Hardware Users
---

### Post by kmand on 2009-10-31
I've run Ubuntu off an external USB hard drive on a Mac Mini for some time. Until now I have been using Legacy Grub with Ubuntu. The only way I have been able to make this work is to have refit boot off a Legacy Grub CD which gets a kernel off a partition on the internal drive, but sets root on the USB drive.

Ubuntu 9.10 offers Grub2 and I'm wondering if I can do something with less pieces. I particularly don't like maintaining a shadow boot partition on the internal disk, or depending on the CD to boot.


I tried just letting Ubuntu 9.10 install with Grub2 on the USB drive. When I boot with refit off the "legacy" partition, I get a screen with "Using Load Option USB", then a dozen lines of not found errors, and finally a line that says that external hard drives are not well supported by Apple firmware.

Is there something else I should try with Grub2, thats an improvement of the awkward setup I use with Legacy Grub?

---

