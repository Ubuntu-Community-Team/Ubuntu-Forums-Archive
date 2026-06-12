---
title: "Device 18 and 19 boot message information"
date: 2007-06-12
forum: Apple PPC Users
---

### Post by thedarky on 2007-06-12
Hi,  I have an answer for the  device 18 and 19 message that a few of us are getting:

Looking at the System Messages Log Viewer, available on the desktop from the System Administration list of utilities, I find that it is not a hardware fault but a recognition that 2 USB controller interfaces on the motherboard have been disabled by the Apple firmware;

> Jun 12 14:51:07 **** kernel: [   35.637315] Apple USB OHCI 0001:10:18.0 disabled by firmware

Jun 12 14:51:07 **** kernel: [   35.637320] Apple USB OHCI 0001:10:19.0 disabled by firmware

So I'm discarding this as a RAM symptom.  It seems that Apple has used the same basic motherboard for several different machines.

---

