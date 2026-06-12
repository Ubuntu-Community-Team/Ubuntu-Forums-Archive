---
title: "Ubuntu Live USB Not Working"
date: 2011-08-12
forum: Apple Hardware Users
---

### Post by avlinx on 2011-08-12
I followed the instructions on the ubuntu website for making a bootable ubuntu usb drive/flash drive for mac compatibility. I tried several times and it wont work. First i tried it with the apple software on booting it up but it didnt detect the usb drive. Next i used refit, which detected it but would take me to a blank screen. i was unable to do anything from there and had to force restart every time i tried. Do you know whats wrong?
here is the link for the guide i followed: [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)
-Thanks
avlinx

---

### Post by pindar on 2011-08-13
Booting Macs from USB is more difficult than it appears at first sight. Different models behave very differently, in an unpredictable manner. I have never been able to boot a mac with a usb made from the guide you mention. That said, there are 2 things you could try which might help: 

[LIST=1]
[*]Try the solution in [this guide]("http://www.devslashzero.com/node/160"). I have been able to boot my MacBook with a usb key made this way.
[*]If this doesn't help, you can also try the EFI method; this has also worked for me. There's a short description I made in an [older post]("http://ubuntuforums.org/showthread.php?p=10478989#post10478989").
[/LIST]
But be prepared to try several times; this can be a frustrating experience. Good luck!

---

### Post by avlinx on 2011-08-13
thanks for ur help

---

### Post by ASchlosser on 2011-08-24
If you're still having issues, try creating a standard USB drive using diskutility and the Ubuntu .iso.  Then burn a PLoP bootcd ([http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)) using diskutility.  Put the flash drive and disk in, shut the computer off completely, then hold down c during a cold boot.  Then once it gets into PLoP, select USB and it'll boot into the USB.  Wham, you're in.

-Andy

---

