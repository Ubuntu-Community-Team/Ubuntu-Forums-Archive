---
title: "3 G data card not working"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by willeb on 2006-12-27
I just installed LTS6.06 from a shipit CD.   This is the second round over the last year trying to get ubuntu working.  Both could not get the modem to function ie no internet connection.   Running a AT/AT compatible with Intel Celeron 2.0 GHz.
Dual boot with XP home and LTS6.06.   Modem is installed on Com 3.   A Vodafone 3G HSDPA data card on a pci cardslot.  Manufacturer is HUAWEI Tchnologies; model E620; Revision 1.11.16.09.00.11; +GCAP: +CGSM, +Fclass, +DS.

I ran # dmesg | -18 with the following result.

lines 17179599;
usbcore: registered new driver usbserial_generic
drivers/usb/serial/usb-serial.c:USB serial driver core
drivers/usb/serial/usb-serial.c:USB Serial support registered for option 3 G data card.
option 7-1:1.0: Option 3 G data card converter detected.
usb 7-1: option 3 g data card converter now attached to ttyUSB0
option 7-1:1.1: Option 3 G data card converter detected.
usb 7-1: option 3 g data card converter now attached to ttyUSB1
option 7-1:1.2: Option 3 G data card converter detected.
usb 7-1: option 3 g data card converter now attached to ttyUSB2
usbcore: regestered new driver option
drivers/usb/serial/option.c: Option card (PC - card to) USB to serial driver : v0.4

With this i assume the system see the card but i cannot get the setup on firefox right to access the net.
I cannot download any other programs to help with the setup.
PSE help

---

