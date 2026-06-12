---
title: "ACPI is going crazy"
date: 2007-12-05
forum: Apple Intel Users
---

### Post by Rog-Mahal on 2007-12-05
Recently, I've been having some problems with acpi causing my laptop to run hot and have had some significant decrease in battery life. I compiled a custom kernel with tickless support and it's been working fine, but here is my powertop output while doing nothing more than using firefox to type this post:

```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (63.4%)         2.17 Ghz     3.5%
C1                0.0ms ( 0.0%)         2.00 Ghz     0.0%
C2                0.1ms (11.7%)         1333 Mhz     0.1%
C3                0.2ms (24.9%)         1000 Mhz    96.4%


Wakeups-from-idle per second : 3024.3   interval: 10.0s
Power usage (ACPI estimate): 24.2W (1.8 hours)

Top causes for wakeups:
  97.2% (6285.0)       <interrupt> : acpi 
   2.0% (131.8)       <interrupt> : uhci_hcd:usb5, i915@pci:0000:00:02.0 
   0.3% ( 22.6)       <interrupt> : wifi0 
   0.2% ( 15.3)       <interrupt> : ehci_hcd:usb1, uhci_hcd:usb2 
   0.2% ( 11.0)       <interrupt> : libata 
   0.0% (  0.7)       <interrupt> : libata, ohci1394, uhci_hcd:usb3

```

Any ideas? I just noticed this recently. Seems like acpi is keeping my cpu running much more than it should.

---

