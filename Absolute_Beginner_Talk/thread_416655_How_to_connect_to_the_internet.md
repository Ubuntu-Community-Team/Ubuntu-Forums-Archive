---
title: "How to connect to the internet"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by mk007 on 2007-04-21
Hi

I am busy downloading ubuntu, and it will be the first time I installed this operating software. I have a Billion ADSL modem. How am I going to install this modem, the drivers that came with it is only for windows.

thanks
Marius

---

### Post by MiCovran on 2007-04-21
If your modem is connected to you LAN, just type 'pppoeconf' in terminal and follow the instructions. It worked for me.

---

### Post by mk007 on 2007-04-21
Thanks

Without installing any drivers?

---

### Post by MiCovran on 2007-04-21
As far as I know, you only need drivers for USB connection, and that's why it doesn't work with linux.

Edit: If it's connected to LAN, it works without drivers in windows too.

---

### Post by mk007 on 2007-04-21
Thanks for your replies.

My modem is a usb modem. You saying that I won't be able to use it?

---

### Post by MiCovran on 2007-04-21
With USB, i don't think so. Check if there's a possibility of connecting it over ethernet (or LAN). If not, I don't know how to help you. Maybe someone else.

---

### Post by trippinnik on 2007-04-21
Can you give me more info about the modem? some are supported in the Kernel, do you have the Feisty live CD already?  If you do try plugging in the modem and typing lsusb in the terminal.  It'll tell you the USb devices connected.  Also type dmesg and it will output some handy info about starting up harware etc.  the last line will correspond to the modem if it was just plugged in.

---

### Post by trippinnik on 2007-04-21
I don't know what model you have but this came up when I&#12288;googled it: [http://www.billion.com/product/adsl/bipac7001.php](http://www.billion.com/product/adsl/bipac7001.php) so maybe it's supported.

---

