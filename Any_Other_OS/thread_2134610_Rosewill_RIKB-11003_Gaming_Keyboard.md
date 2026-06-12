---
title: "Rosewill RIKB-11003 Gaming Keyboard"
date: 2013-04-11
forum: Any Other OS
---

### Post by regor210 on 2013-04-11
I purchased a Rosewill RIKB-11003 Gaming Keyboard with Programmable Keys from Ebay.

It works fine in Grub and in my BIOS.

In LinuxMint Maya 13 using kernel 3.2.0-39-generic #62-Ubuntu SMP I get

$ lsusb
Bus 002 Device 003: ID 04d9:a055 Holtek Semiconductor, Inc.

$ lsusb -v
Bus 002 Device 003: ID 04d9:a055 Holtek Semiconductor, Inc. 
Couldn't open device, some information will be missing.......

There's not much about getting this keyboard working in Linux on the web but after much searching and trial and error this is what works

Ubuntu 13.04 (dev) using  3.8.0-17-generic
Kanotix using kernel 3.8.2-2-486....

Not working
Ubuntu 12.04  using  kernel 3.2.0
Ubuntu 12.10 using   kernel 3.5.0

In short the older kernels do not support  the Rosewill RIKB-11003 keyboard so if your new to GNU/Linux Ubuntu LinuxMint I would recommend waiting a bit and upgrading to Ubuntu 13.04 when it comes out later this month.

---

### Post by RosewillEye on 2013-04-12
Thanks for using the RIKB-11003 Gaming Keyboard from Rosewill. Did you get everything working?

---

