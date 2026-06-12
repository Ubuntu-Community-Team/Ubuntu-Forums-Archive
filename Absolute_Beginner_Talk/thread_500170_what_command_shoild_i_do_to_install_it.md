---
title: "what command shoild i do to install it"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by arif9k on 2007-07-13
i have downloaded the filewhen i was surfing in windows named- rconnect-cmdline-1.0- it is a file for the installation of wireless modem .

but what command shoild i do to install it

---

### Post by Happy_Man on 2007-07-13
Generally, you can't use Windows drivers under Ubuntu. To get your wireless modem working, have you considered Ndiswrapper?

---

### Post by wildseven on 2007-07-13
> **Happy_Man said:**
> Generally, you can't use Windows drivers under Ubuntu. To get your wireless modem working, have you considered Ndiswrapper?

Yup you are correct. To use windows driver you MUST use ndiswrapper. It is a hassle to do. Just get yourself a pcmcia card or usb wifi.

---

### Post by ReaderRat on 2007-07-13
Check out the wireless network cards that work:  [Network Card Support](https://help.ubuntu.com/community/HardwareSupport)

---

### Post by Warren Watts on 2007-07-13
> **arif9k said:**
> i have downloaded the filewhen i was surfing in windows named- rconnect-cmdline-1.0- it is a file for the installation of wireless modem .

but what command shoild i do to install it

I think what he meant was he was surfing IN WINDOWS (since he didn't have a Linux driver for his wireless modem) and he downloaded a Linux driver called rconnect-cmdline-1.0.tar.

I did a little research, and here is a quote from the originating website:

> Reliance Netconnect for Linux

This is a beta release of the Reliance Netconnect driver for **Linux OS Red Hat Version 8.0** and is available to the user on an "as-is-where-is’ basis. This driver is unsupported and is provided to the Linux user community as a courtesy. Reliance does not provide any support or warranty for this driver and will not undertake any liability for use of this software.

[B]System Requirements

Linux 8.0 Red Hat[/B]

It looks like your driver is for RedHat, dude.  I'm not edumacated enough to be able to tell you if it will work in Ubuntu.....

---

### Post by Happy_Man on 2007-07-13
He could use alien to convert the package.....

---

