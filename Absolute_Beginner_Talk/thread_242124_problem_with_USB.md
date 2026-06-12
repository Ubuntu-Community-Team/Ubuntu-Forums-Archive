---
title: "problem with USB"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by bloody_tears on 2006-08-23
I have my mob. phone Siemens c75 and usb cable. How can I make connection with my phone?? the original cd contains only software for windows.

---

### Post by kidders on 2006-09-03
What exactly do you mean by "connect"? Perhaps what you're after is a serial terminal, that would let you do things like sync your phone book, send messages or make calls.

To do this, you need to create /dev entries that usually look like "ttyUSBx". USB serial drivers do this for you, in much the same way my bluetooth one (called "rfcomm") can. Once you've managed that, you can point any one of a number of generic mobile phone tools at the serial "port" and get them talking to your phone.

It's quite possible Ubuntu is auto-loading the kernel modules necessary to set up a serial connection with your phone. Type **dmesg** into a terminal window to check for stuff like:

```

usb 2-1: new full speed USB device using ohci_hcd and address 3
drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
usbcore: registered new driver usbserial_generic
usbcore: registered new driver usbserial
drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
drivers/usb/serial/usb-serial.c: USB Serial support registered for PL-2303
pl2303 2-1:1.0: PL-2303 converter detected
usb 2-1: PL-2303 converter now attached to ttyUSB0
usbcore: registered new driver pl2303
drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor
driver v0.12

```

If something like this is happening, you're in business! Post back and we'll see where to go from ... well ... wherever you're at :)

---

