---
title: "Absolutely Flummuxed!!"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-03-07
Hi

For those of you kind enough to help, please explain in Lady Bird language, this is my first time ever with Linux.

I appear to be getting stuck at the same point every time and can't figure out how to get the GUI, despite hours and hours of trawling for an answer.  Basically, I'm installing Ubuntu (AMD64 version) onto a homebuilt machine with an AMD Athlon 64bit CPU, an ASUS AN8-E motherboard, a Radeon X550 PCI-Epress 256 DDR graphics card, an 80 gig HD and 1 gig of RAM.  Each time, however, I end up at the same place... 'username@ubuntu:$'.  I have tried 'sudo startx', also tried 'sudo apt-get xubuntu-desktop' and tried 'sudo dpkg-reconfigure xserver-xorg'.  I tried using the 'versa' driver and playing around with other setting, as it appears my card is not supported.  I have also tried installing the 32bit version of Ubuntu, but ended up at the same point!

The other options are to stick with XP or throw the damm lot out of the window.  Please help  :confused: 

Regards

---

### Post by TrendyDark on 2006-03-07
I'm not entirely sure that the video card you have is supported, although it should at least try and start the Xserver before throwing you into a CLI interface.

EDIT: Upon looking at the ATI Website, it seems that the catalyst driver supports some PCI-E cards. So many try the instructions on installing the newest catalyst drivers. You should be able to do this from a CLI interface if you have an internet connection.

The link is in my signature.

---

