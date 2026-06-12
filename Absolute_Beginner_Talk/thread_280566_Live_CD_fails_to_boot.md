---
title: "Live CD fails to boot"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by grrizd67 on 2006-10-19
It gets to the end of the bootup and reports X drive failure. Any ideas?](*,)

---

### Post by Kateikyoushi on 2006-10-19
Most likely you have to pass some options at boot. I would try the safe video mode.

At menu F6 then start with these options

Boot: linux noapic (especially if you have a Pentium IV or newer Pentium class processor)
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

If these still do not help you can try the alternate install cd.

---

