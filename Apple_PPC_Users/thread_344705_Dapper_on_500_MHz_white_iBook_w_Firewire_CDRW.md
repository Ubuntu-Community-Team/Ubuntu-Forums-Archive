---
title: "Dapper on 500 MHz white iBook w/ Firewire CD/RW"
date: 2007-01-23
forum: Apple PPC Users
---

### Post by katsumi on 2007-01-23
Hello,

Has anyone experienced a problem of a Firewire CD/RW drive not showing up when running 6.06 on a PPC iBook? The dmesg looks a little strange at boot:

[   42.109817] ieee1394: Initialized config rom entry `ip1394'
[   42.121103] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   42.124677] ohci1394: fw-host0: Unexpected PCI resource length of
1000!
[   42.175038] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]
MMIO=[f5000000-f50007ff]  Max Packet=[2048]
[   70.243740] ieee1394: sbp2: Driver forced to serialize I/O
(serialize_io=1)
[   70.243750] ieee1394: sbp2: Try serialize_io=0 for better performance

Then, when i connect or disconnect the drive nothing happens and it doesn't show up. Any ideas?? :):KS

---

