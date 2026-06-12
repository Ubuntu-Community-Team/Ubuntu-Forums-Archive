---
title: "booting from USB pendrive at ibook G4"
date: 2007-04-01
forum: Apple PPC Users
---

### Post by ik80 on 2007-04-01
Hi,
is there a way to boot Ubuntu (Feisty beta or Edgy) from a 1GB USB pendrive in my iBook G4 1.2GHz?

I found [this tutorial for x86 (link here)]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar"), would this work using the PPC liveCD? 

thanks in advance

---

### Post by walter_f on 2007-04-01
> **ik80 said:**
> Hi,
is there a way to boot Ubuntu (Feisty beta or Edgy) from a 1GB USB pendrive in my iBook G4 1.2GHz?

I found [this tutorial for x86 (link here)]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar"), would this work using the PPC liveCD? 

thanks in advance

It is not possible to boot any Mac PPC (like your iBook G4) from a USB drive, be it hard disk or flash memory, under Mac OS. 

As this seems to be a hardware limitation, you won't be able to boot a Mac PPC using Ubuntu on a USB drive, either.

Try Firewire (yes, there are Firewire flash memory sticks. However, they are not cheap...)

;-)

Walter.

---

### Post by didg on 2007-04-01
you can't boot the liveCD out of the box but it's doable.

First if you want to double check that your iBook boot from USB you can download pprcd rescue CD from [http://ppcrcd.pld-linux.org/](http://ppcrcd.pld-linux.org/), it's small (50MB) and should boot out of the box (press alt  on startup, choose the linux icon, done).

For Ubuntu the easiest (IMO):

- from linux or ÒSX copy with dd the liveCD on your USB stick, this will destroy whatever you have on your stick.

- follow 'Booting from USB memory stick' at [https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html)
on how to find the OpenFirmware pathname of your USB stick

Note:
boot usb0/disk:,\\:tbxi
Will not work with the default liveCD because the script ofboot.b is using the wrong alias cd:, I hope we can fix it for feisty release.

rather use
boot usb0/disk:,\install\yaboot
 
of course replace usb0/disk with whatever you get from dev / ls and devalias.

---

### Post by ik80 on 2007-04-02
thanks for the infos.
gonna tried it out.

---

