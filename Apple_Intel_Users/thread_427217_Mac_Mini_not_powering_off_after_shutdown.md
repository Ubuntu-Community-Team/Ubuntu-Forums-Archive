---
title: "Mac Mini not powering off after shutdown"
date: 2007-04-29
forum: Apple Intel Users
---

### Post by minty on 2007-04-29
Hi,

Feisty on an Intel Mac Mini.

Running:

  sudo shutdown -h now

or

  sudo reboot

Does everything, including turning the light on the front off, but never quite fully powers the machine off.  I have to hold the power button on the back down for about 5 seconds to actually properly turn it off.

Any pointers on how to fix that?

---

### Post by minty on 2007-04-29
It would seem like it is related to a (Freecom) USB DVB-T (Freeview) stick.

If I un-plug that, then it is able to power off completely.

So I guess the next problem is how to sufficiently disconnect that usb device just before I shutdown so that it doesn't continue to hang it.

---

### Post by minty on 2007-04-29
I think I've fixed this by doing the following

sudo echo "/sbin/rmmod usbhid" > /etc/rc0.d/K99usbhid
sudo echo "/sbin/rmmod dvb_usb_dtt200u" >> /etc/rc0.d/K99usbhid
sudo chmod u+x /etc/rc0.d/K99usbhid
cp /etc/rc0.d/K99usbhid /etc/rc6.d/K99usbhid

I think the usbhid line may well be redundant - by removing the usb dvb-t module at the very end, it appears to be able to shut off the power correctly.  So Shutdown works.

Rebooting still fails - it power cycles, but then is unable to begin the boot process.  Just hangs after the Apple "boing".

fwiw, I'm not using BootCamp or Parallels, just a fresh/full install of Feisty

---

