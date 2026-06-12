---
title: "Tripple boot problem"
date: 2010-12-06
forum: Apple Hardware Users
---

### Post by jered6323 on 2010-12-06
Mac OS X installed first
Windows 7 - Bootcamp installed second
Ubuntu 10.10 installed third.
rEFIt installed prior to Ubuntu as recommended.

I installed Ubuntu and could boot just fine, but I didn't want to keep rEFIt around (VMWare Fusion didn't play nice) so I removed it, restored the Windows bootloader, and used EasyBCD to add an Ubuntu entry to Windows. That way I could also boot Ubuntu inside VMWare if I needed to. Problem is, When I select Ubuntu from the Windows boot menu, it boots to command line grub4dos.

How can I have my computer load Grub2 when I select Ubuntu from the Windows boot menu? (I want to keep Grub2 for the recovery options and such)

---

