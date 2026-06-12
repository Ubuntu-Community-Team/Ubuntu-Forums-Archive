---
title: "My iPod crashes Ubutnu"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-09-28
Whenever I plug in my iPod, all my desktop icons disappear, and after a few seconds Ubuntu crashes and I have to restart my computer.  Why is this?  I don't need to add any songs to it or anything, I just need to charge it sometimes.

Thanks.

---

### Post by SunnyRabbiera on 2007-09-28
hmm, well feisty fawn is pretty bleeding edge.
is this a newer ipod or an older one?

---

### Post by Yes on 2007-09-28
It's a mini, about three years old.  Would Feisty Fawn really be considered bleeding edge?  In less than a month it won't even be the most recent version...

---

### Post by SunnyRabbiera on 2007-09-28
its still bleeding edge so its still going to be unstable, latest doesnt always mean greatest.
have you tried older versions of ubuntu or try another distribution to see how this acts?
the good thing about linux is that a lot of the popular distros out there use live CD's so you can try your ipod and see what it does on the live.

---

### Post by tgalati4 on 2007-09-28
Post the output of:

>cat /proc/interrupts

I'm guessing that the USB interrupt is being shared with something else that causes a system hang.  It should be fixable, although I've never heard of USB device hang a machine.

Which reminds me.  I have an old mini that has a dud battery.  When I plug it in, I get an error message in dmseg  "Overcurrent warning on Port 3, USB . . ."

It's possible that your mini battery is shot and the current draw to charge the battery is clobbering your motherboard.  When 5 volts dips to 4.8 volts, then strange things happen.

Try charging with another device (perhaps a wall charger).  Once charged, then plug it in and see if it works properly.

Or:  Get with Apple's program.  Toss it and buy a new one.  Give the old one to a Linux user--they'll know what to do with it.

---

### Post by tech9 on 2007-09-28
> **Yes said:**
> Whenever I plug in my iPod, all my desktop icons disappear, and after a few seconds Ubuntu crashes and I have to restart my computer.  Why is this?  I don't need to add any songs to it or anything, I just need to charge it sometimes.

Thanks.

try upgrading Gutsy Gibbon... my ipod works flawlessly on 7.10

---

### Post by Yes on 2007-09-30
Here's my cat /proc/interrupts :

```
           CPU0       CPU1       
  0:      52382          0   IO-APIC-edge      timer
  1:        247          0   IO-APIC-edge      i8042
  6:          5          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          3          0   IO-APIC-edge      rtc
  9:          1          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      libata
 15:       3501          0   IO-APIC-edge      libata
 16:       1027          0   IO-APIC-fasteoi   libata, uhci_hcd:usb4, eth0
 17:      58705          0   IO-APIC-fasteoi   ehci_hcd:usb1
 18:          3          0   IO-APIC-fasteoi   ohci1394
 19:      17088          0   IO-APIC-fasteoi   uhci_hcd:usb2, uhci_hcd:usb5, radeon@pci:0000:01:00.0
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 21:       1334          0   IO-APIC-fasteoi   EMU10K1
NMI:          0          0 
LOC:      52255      52255 
ERR:          0
MIS:          0
```

My battery seems fine (It lasts as long as it ever did), and it's in pretty good shape.  Getting a new one is out of the question.

---

