---
title: "Can't boot into recovery mode"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Jugney on 2007-12-24
Hey everyone,

I can't get into recovery mode to configure Xorg. When I try to boot into Recovery Mode, it freezes at the following lines:

[ 0.552000] Enabling IO-APIC IRQ
[ 0.552000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

When I grappled with getting my nVidia drivers working on my first install I could get around this by booting from my text install CD (LiveCD didn't work), then pressing CTRL+ALT+DELETE to reboot. I took out the CD to get the regular boot menu and then I could get into recovery mode. But that doesn't work anymore.

This makes me grateful I've got a dual boot with Windows so I can ask you guys!

Any ideas?

Jugney

---

### Post by Maxtorm on 2007-12-24
Does disabling APIC help? When you're on the grub menu, cursor down to the Recovery Mode line and type e to edit. Cursor down to the line that starts with "kernel" and type e again. Add "noapic" at the end of the line and hit Enter. Type b to boot with these options.

---

### Post by Jugney on 2007-12-25
Thanks! That works.

Jugney

Happy Holidays

---

