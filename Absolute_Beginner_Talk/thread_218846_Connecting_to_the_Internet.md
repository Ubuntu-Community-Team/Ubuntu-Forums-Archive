---
title: "Connecting to the Internet"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Gris on 2006-07-19
Hi Everyone

I'm trying to connect to the Internet using a DWL-120b wireless USB interface.

I can't install linux-wlan-ng because I get the error message:

* linux >= 2.6.13-rc1 requires pcmciautils instead of pcmcia-cs

I'm stuck! I tried "dmesg | grep prism" and got:

prism2usb_init: prims2_usb.o: 0.2.2 Loaded
prism2usb_init: dev_info is: prism2_usb
usbcore: registered new driver prism2_usb
prism2sta_ifstate: hfa384x_drvr_start() failed, result=-5

Can anyone help me please?

David

---

### Post by ellion on 2006-07-19
Already tried installing pcmciautils? I guess it will be most likely replacing pcmcia-cs.

sudo aptitude install pcmciautils

---

### Post by Gris on 2006-07-19
Hi Ellion

I tried running that and get output which says:

"No packages will be installed, upgraded, or removed."

It seems to indicate it is already installed?

What can I try to check the installation?

David

---

### Post by drtvasudevan on 2006-07-19
thought gris has problem connecting to internet!
how to sudo apptitude.....

---

### Post by Gris on 2006-07-19
I really have no idea how to proceed! Is there any guide to wireless networking I could follow?

David

---

