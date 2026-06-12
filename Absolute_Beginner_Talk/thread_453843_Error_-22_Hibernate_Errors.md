---
title: "Error -22? Hibernate Errors"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by vertexoflife on 2007-05-24
Occasionally coming out of and going into hibernate I will see the following message:

[159245.636000] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt. Error: -22

Sometimes going into hibernate, my entire screen will fill up with a ton of code, an example of which follows:

[159520.988000] hub 1-0:1.0: PM: suspend 2->1 parent usb1 already 2
[159520.988000] usbdev1.1_ep00: PM: suspend 0->1 parent usb1 already 2

And occasionally, coming out of hibernation I get the message:

Starting up...
[        0.0709261] PCI: BIOS BUG #81[49435000] found.

These messages are the only problem I seem to be having, and nothing else seems to be wrong. I think it had something to do with BIOS or the eth0/eth1/eth2 things on this OS.

I'm running Ubuntu 7.04 on a Toshiba Tecra laptop.

Any solutions available?

---

### Post by Flump5000 on 2007-05-25
yeah i had the same problem when i put my computer in hibernate last night. and then when i rbooted it this morning i just got a command prompt kind of thing. it worked when i turned it off and back on but i dont know why it did it or if it will do it again.

---

### Post by vertexoflife on 2007-05-25
Other than that, no one understands this endless code?

---

### Post by culorut on 2007-06-02
I also receive **[0.0709261] PCI: BIOS BUG #81[49435000] found** upon startup as well.

I am running Ubuntu 7.04 on a Toshiba Satellite s4527. The laptop runs fine but I cannot find any information regarding this error on these forums or the web.

One post I read mentioned to update the bios but Toshiba only has bios updates for MS Vista. I read about adding the noacpi to grub but I am not sure I want to turn anything off that should be running.

---

