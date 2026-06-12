---
title: "Error Code on install, Can someone help!"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by videoman32 on 2007-12-07
I keep getting this message when I try to boot up Ubuntu..........


0.436000 ..mp bios bug:8254 timer not connected to IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option

Please help!

---

### Post by Partyboi2 on 2007-12-07
try adding noapic to the boot options and see if that works.
When grub is loading hit esc then highlight the line that says kernel        /boot/vmlinuz-2.6.22-14-generic root (or something like that, should be the first one) press e to edit then at the end of the line add noapic then press enter then b to boot, if this works then you can add it to grub to boot like that always.
You might also be able to disable apic in the bios depending on the type of setup you have.

---

