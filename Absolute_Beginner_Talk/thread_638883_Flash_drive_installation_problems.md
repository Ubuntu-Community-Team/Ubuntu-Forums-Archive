---
title: "Flash drive installation problems"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by OttoDestruct on 2007-12-12
I used the guide from here:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

and was able to make (I think) make a flash drive correctly, however I'm still having problems. I'm having trouble verifying it as my main desktop doesn't seem to want to boot from flash drives at all (running an Asus A7N8X mobo if anyone knows the trick to get it to work).

When I go to boot on the laptop (Dell Inspiron 1000) it accesses the flash drive, but I get this message:
> 
Pen Drive Without Operating System. Remove Pen Drive And Reboot.

Intel UNDI PXE-2.0 (build 082)
Copyright 1997-2000 Intel Corporation

SIS 9000 PXE BootROM v1.09b Hook Int18

Client Mac Address: mac address here GUID: lots of numbers here
PXE-E5: No boot filename received
PXE:M0F: Exiting Intel PXE Rom.


After this message it just sits there until I reboot.


Did I make the flash drive wrong, or do I need to install Lilo on the flash drive like it says?

---

### Post by OttoDestruct on 2007-12-12
Just tried installing lilo, where I get this:

> root@ubuntu:/home/ubuntu# lilo -M /dev/sda1
Fatal: /dev/sda1 is not a master device with a primary parition table


Edit: nevermind found my error with this, off to test my luck again

---

