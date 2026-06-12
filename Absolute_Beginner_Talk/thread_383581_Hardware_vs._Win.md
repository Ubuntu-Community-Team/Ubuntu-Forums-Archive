---
title: "Hardware vs. Win"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by bks on 2007-03-13
What is the difference between a hardware modem and a winmodem?

---

### Post by kolinab on 2007-03-13
"A Softmodem is a software modem designed to use a host computer's resources (mostly CPU power and RAM but sometimes even audio hardware) instead of dedicated hardware of its own, unlike traditional modems." [wikipedia]

[http://en.wikipedia.org/wiki/Softmodem](http://en.wikipedia.org/wiki/Softmodem)

---

### Post by bks on 2007-03-13
I've got a PCI modem that, according to scanModem, is a winmodem.  A PCI modem is hardware modem, with its own chipset, is it not?  Does it still require the use of the PCs resources to operate? I guess maybe I'm just being dense, but it is confusing to me.

---

### Post by gh0st on 2007-03-13
It sounds like winmodem is just the name of the manufacturer of your modem, I think because you asked if it was different to hardware it confused people a bit and thats how softmodems got brought up. A software modem is as described above, a virtual modem but it sounds like you have a normal PCI modem which is hardware.

I think there were some crossed wires there. Your PCI modem has it's own chipset and resources  on board so it doesn't use the systems resources in the same way as a softmodem at all. It just uses the PCI connections on the motherboard to talk to the rest of your system. Does that help explain it at all?

That's probably not the clearest explanation but hopefully it is of some use to you :)

---

### Post by serag on 2007-03-13
a hardware modem has all needed chips on board the PCI card.  A winmodem is still a PCI card, with chips on it, but it offloads the majority of the real work to the cpu, instead of dedicated onboard chips.

---

### Post by bks on 2007-03-13
> **serag said:**
> a hardware modem has all needed chips on board the PCI card.  A winmodem is still a PCI card, with chips on it, but it offloads the majority of the real work to the cpu, instead of dedicated onboard chips.

OK, that makes sense. Anyway the reason I ask is because I'm having a heck of a time getting my modem to work. I'm totaly confused on how to compile the driver, but that's for a whole other thread. Thanks for the help!

---

