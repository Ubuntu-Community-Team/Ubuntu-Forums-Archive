---
title: "Determining Virtual Com Port number FTDI driver"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by bungnati on 2007-10-07
Hi im using Ubuntu 7.04 FF. Im also using a virtual com port(VCP) driver from ftdi. How would I find the VCP number assigned to the device im using? Im new to linux (6 days) I know in windows i can find it under the hardware manager but cant find it under Ubuntu's "Hardware Information" I have also tries the "lsusb" terminal command and cant determine it.

Thanks 
John

---

### Post by Anders J on 2007-11-27
Once You've sorted out the brltty bug (search and You will find), just plugging in the FTDI device cable will make this port visible as /dev/ttyUSB0 (probably incrementing if You connect more devices).

---

