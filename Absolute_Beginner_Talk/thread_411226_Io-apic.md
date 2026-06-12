---
title: "Io-apic"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Siberia on 2007-04-16
After running: gksudo "update-manager -c -d" from Ubuntu 5.1 to upgrade (which I have done once before and had the same problem but fixed, can't remember how though) I get the message on boot:

MP-BIOS bug:8254 timer not connected to IO-APIC
Kernel panic -not syncing:IO-APIC + timer doesn't work!

And the boot continues no further.

Any ideas?

---

### Post by bashologist on 2007-04-16
I had the same problem when trying to install Debian Etch stable just after its release. I tried again with the boot options:
```
install apic="debug"
```Then it worked, but only one of my two cpu's is visible. Maybe I should add noapic or something to menu.lst?

Did your message look anything like this?
[[IMG]http://img151.imagevenue.com/loc476/th_58197_DSC02895_122_476lo.JPG[/IMG]](http://img151.imagevenue.com/img.php?image=58197_DSC02895_122_476lo.JPG)

What're you computer specs?

Here are my specs:
Processor: AMD Athlon 64 X2 Dual--Core Processor 4200+ for TRUE Multi--tasking AMD Live, 2.2GHz, 512KB+512KB L2 Cache
Memory: 1024MB PC2--4200 DDR2 SDRAM memory (expandable to 2GB)
Graphics card: Integrated GeForce 6150LE Graphics with up to 256MB shared video memory

---

### Post by Siberia on 2007-04-16
Everything above the kernel panic I didn't receive although same button message. I have the same processor and 1Gb DDR2 RAM with a nVidia 7600 GT 256Mb graphics card although it was only a quick install on an old hard drive and I found a copy of 6.06 laying around so I'm installing with that instead I'll keep that install option in mind though. Thanks bashologist.

No need for further posts (I Hope). Thank you.

---

### Post by UbuntuniX on 2007-04-17
> **bashologist said:**
> Here are my specs:
Processor: AMD Athlon 64 X2 Dual--Core Processor 4200+ for TRUE Multi--tasking AMD Live, 2.2GHz, 512KB+512KB L2 Cache
Memory: 1024MB PC2--4200 DDR2 SDRAM memory (expandable to 2GB)
Graphics card: Integrated GeForce 6150LE Graphics with up to 256MB shared video memory

I have more or less the same, except being a 3800+ and ATi graphics.

This problem (almost) always arises after a distro installation, boot with the noapic option.
For example:
Press F6 (I think) on the ubuntu boot screen, and type "noapic" at the end of the line.
On Debian 4.0, it worked as "installgui noapic".

Good luck to you.

---

