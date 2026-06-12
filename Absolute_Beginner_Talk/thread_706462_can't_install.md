---
title: "can't install"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by bigoutcast on 2008-02-24
hi just downloaded ubuntu 7.10 and tried to install started to boot and went to main install screen. pressed enter to run install something loaded in about 2/3 seconds went to 100% then screen went blank hard disk was still running. i have core2duo cpu sata hdd xfx m/b xfx f/x card 4gb ddr2 ram thanks for looking

---

### Post by bobbybobington on 2008-02-24
try adding the following to the boot parameters
```
linux vga=771 acpi=off noapic nolapic
```

---

