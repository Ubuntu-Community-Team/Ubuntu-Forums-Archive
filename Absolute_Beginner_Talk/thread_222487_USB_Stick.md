---
title: "USB Stick"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2006-07-25
I have just installed Dapper on my Altos 600 PC. It was a fresh installation and completely over-wrote my previous Ubuntu. But now my USB stick is not recognised. Any ideas?

---

### Post by Lord Illidan on 2006-07-25
Have you tried entering ```
dmesg
``` in a terminal when you put in the USB stick? Examine the last few lines of output, if necessary copy them here.

---

### Post by cairnsww on 2006-07-25
I have done tywo things - 

Re-installed 5.04 and sure enoughthe usb stick does work.

Re-re-installed 6.06 and sure enough it still doesn't.

dmesg does not seem to tell me much. The last four lines have nothing to do with usb - but might indicate an error: irq errors.

Wrt usb it says (much higher):

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface Driver v2.3

Followed immediately by a possible error (?)

****SET: Misaligned resource pointer: cfed 43e2 Type 07 Len 0

A possibel problem here is that the usb ports are UBS 1.1, not 2. It is an old machine.

---

