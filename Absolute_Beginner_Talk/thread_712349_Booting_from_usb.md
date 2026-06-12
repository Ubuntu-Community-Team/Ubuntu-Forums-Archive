---
title: "Booting from usb"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-03-01
I'm attempting to boot linux from USB on a friends computer but I'm guessing the BIOS doesn't support it for there is no option to boot from USB anywhere in the boot screen. 

The system being used is XP prof. My guess is that the computer wasn't installed with BIOS when it was made. It's an HP Omnibook 6100. 

My Thumb is recognized when I boot into XP.

Any suggestions? Install BIOS?????

---

### Post by ssharps711 on 2008-03-01
Ok, nm that was dumb. Anyhow, I'm still stuck because I can't figure out how to boot from the USB once I get into BIOS.

---

### Post by Victormd on 2008-03-01
Once in the BIOS, look for boot options or boot order and check to see if you can boot from the USB. If there's nothing under the boot menu that allows you to choose USB, then it's not supported. Usually, you can choose the boot device by pressing the F12 (Boot menu) key during boot up on HP laptops (at the same time you would press DEL to enter BIOS setup). Check to see if USB is an option.

---

### Post by mikeyphi on 2008-03-01
If you get into BIOS then look at drives - if the USB is recognised it will be listed. If listed you can select it as first boot option.

---

### Post by Diabolis on 2008-03-01
There is no such a thing as pc without a bios, its the most basic software it needs to start up. I haven't tried to boot from a usb yet, but this link might point you into the right direction:

[http://www.cyberciti.biz/tips/howto-linux-bootable-usb-pen-harddisk.html](http://www.cyberciti.biz/tips/howto-linux-bootable-usb-pen-harddisk.html)

Also this could be of your interest:

[http://damnsmalllinux.org/usb.html](http://damnsmalllinux.org/usb.html)

---

