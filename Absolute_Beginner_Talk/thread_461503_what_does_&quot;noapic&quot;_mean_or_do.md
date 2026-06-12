---
title: "what does &quot;noapic&quot; mean or do?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by residualbit on 2007-06-01
i had problems with my computer freezing i added this to boot and it fixed it, just wondering what it does....would it affect recording?

---

### Post by owise1 on 2007-06-01
Are yiu sure you used noapic  - see comments from another post i found when I googled noapic.

Relates to how the programable interrupt controlled works ( old ones only had 16pins and limited the number of devices that could be serviced.

"With NOAPIC, the old PIC is used for interrupt delivery. It only has 16 pins, most of which are reserved for legacy ISA devices, so PCI devices end up sharing pins. Moreover it only delivers interrupts to the BSP (CPU 0).

Without it, the IOAPICs are used for interrupt delivery. You usually then get several dozens pins and delivery to any CPU.

NOAPIC should never be used. It is not supported. It is only available for some emergency debugging. It will be removed eventually. ESX uses IOAPICs (in the current release). Note that even in the case of the truncated MPS table mentionned above for HP servers, IOAPICs are used.

As for ACPI, there is no power management in ESX. The ACPI tables are unused (in the current release). "

---

### Post by owise1 on 2007-06-01
Maybe I should have been a bit clearer - read my post after I posted it!

APIC: Advanced Programmable Interrupt Controller
ACPI: Advanced Configuration and Power Management 

Disabling ACPI can get some PCs away due to the way power management is handled.

Cheers

---

