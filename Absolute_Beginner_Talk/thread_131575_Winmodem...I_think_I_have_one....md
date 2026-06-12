---
title: "Winmodem...I think I have one..."
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by HSSsb17 on 2006-02-16
Ok...I am running Kubuntu Breezy.  I need to connect to the internet with my 56k modem.  I have a Lucent/Agere Winmodem, driver 8.31.0.0.  Kppp doesn't do the trick.  I read somewhere that I need a chipset or something.  I have no idea how to use the command line thing, or how to install things period.  I just installed Kubuntu last week, and I have no clue how to set up internet or anything, since pretty much everything requires the internet apparently.  I need a thorough walk-through sorta thing, because I am impatient and I haven't found anything good online (which I'm sure there is...).  I would greatly appreciate help.  Thank you!

---

### Post by az on 2006-02-16
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

Scroll down to the "Modems supported by the Lucent driver" part...

---

### Post by HSSsb17 on 2006-02-19
Ok...the DialupModemHowto...still having problems.

I get to this part:

"Now load the drivers for the first time:
  $ sudo modprobe lt_serial
  $ sudo modprobe lt_modem
This should have created the device /dev/modem and you can now go on to configure your dialup connection.
***_No, I get an error about "FATAL: module not found" for this step :(_***
Note for "5.04 Hoary" users: Ubuntu 5.04 Hoary was shipped with kernel 2.6.10, which has some problems with these modules. To fix, change the grub boot commands /boot/grub/menu.lst as follows (pci=routeirq is new):
  ## ## Start Default Options ##
  ## default kernel options
  ## default kernel options for automagic boot options
  ## If you want special options for specifiv kernels use kopt_x_y_z
  ## where x.y.z is kernel version. Minor versions can be omitted.
  ## e.g. kopt=root=/dev/hda1 ro
  # kopt=root=/dev/hda1 ro pci=routeirq
Do not forget to update grub: $ sudo update-grub"

I did the grub thing, but no good.  I read that page countless times (to make sure I wasn't missing anything).  It keeps giving me that "FATAL: module not found" crap.  Is there any easier/better ways to accomplish this?

---

