---
title: "Ubuntu on Macbook Pro - touchpad sometimes doesn't work"
date: 2021-08-23
forum: Apple Hardware Users
---

### Post by tmvaz on 2021-08-23
I've just installed Ubuntu alongside MacOS on my Macbook Pro. I'm new to Linux and I'm looking forward to make a full transition to it - but I'm firstly learning to use it and solve some of the issues I find.

However, sometimes the trackpad doesn't work when booting Ubuntu. The trackpad doesn't respond (but the keyboard is always fine) and I need to plug a USB mouse in order to control the cursor.

My Kernel version is `5.11.0-31-generic`. I already tried the solution provided in [https://unix.stackexchange.com/questions/616033/macbook-pro-2017-trackpad-not-working-sometimes-with-dual-boot](https://unix.stackexchange.com/questions/616033/macbook-pro-2017-trackpad-not-working-sometimes-with-dual-boot) but I got the error:
> 
Error! Bad return status for module build on kernel: 5.11.0-31-generic (x86_64)  Consult /var/lib/dkms/applespi/0.1/build/make.log for more information.

If it helps, my `hwinfo` gives to the keyboard:
> 
> 53: PS/2 00.0: 10800 Keyboard   [Created at input.226]   Unique ID:
> c3zD.Svno16mO_84   Hardware Class: keyboard   Model: "Apple SPI
> Keyboard"   Device: "Apple SPI Keyboard"   Compatible to: int 0x0211
> 0x0001   Device File: /dev/input/event4   Device Files:
> /dev/input/event4,
> /dev/input/by-path/pci-0000:00:1e.3-platform-pxa2xx-spi.3-cs-00-event-kbd
> Device Number: char 13:68   Driver Info #0:
>     XkbRules: xfree86
>     XkbModel: pc104   Config Status: cfg=new, avail=yes, need=no, active=unknow

---

