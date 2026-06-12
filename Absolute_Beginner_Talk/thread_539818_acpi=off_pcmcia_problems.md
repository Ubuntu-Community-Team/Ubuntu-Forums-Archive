---
title: "acpi=off pcmcia problems"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by csixx on 2007-08-31
I have xubuntu (dapper) installed on my older Sony Vaio pcg-fx120.

I had to add acpi=off to the boot options before install would run, and it's also necessary to have it in my grub menu.lst. Without it, the system boots up, but the screen is entirely black. (I can hear the login sounds once its booted up, I just cant see the screen)

The only problem is that with acpi=off, the pcmcia card (wireless network card) does not work.
After plugging the card in, dmesg says something along the lines of "Cardbus not supported".

Is there a way to figure out what part of acpi is failing and just disable that rather than turning acpi off completely?

Or, can i enable the pcmcia slots with acpi=off?

Any help is appreciated.

---

### Post by alienexplorers on 2007-08-31
Is there a way of selecting ACPI =ON in your Bios.

---

### Post by csixx on 2007-08-31
Thanks for the help.

My bios did not have any options for ACPI, so I went looking for a bios update. 

Sony's site had an update to fix some random windows problems so I downloaded it and did the flash.

Afterwards, the laptop boots perfectly without the need for acpi=off, and the wireless card works like a champ.

So, for anyone that has a Sony Vaio PCG-FX120, download the bios update from sony's site (you need winxp installed on the actual laptop to even create the boot floppy), flash the bios, and you will be good 2 go...

Thanks again.

---

