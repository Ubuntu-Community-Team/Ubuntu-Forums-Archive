---
title: "Possible IRQ Problem"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2007-01-17
Ok, i just installed a new intel 3945abg wireless (pci-e) card in my laptop.  after booting up, it didnt show up in lspci.... so i was just trying to investigate and i ran "dmesg | grep "pci""

heres the output
```
rmorris@lappy:~$ dmesg | grep "pci"
[17179574.040000] ACPI: bus type pci registered
[17179574.176000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.176000] pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
[17179574.176000] Allocate Port Service[pcie00]
[17179574.176000] Allocate Port Service[pcie03]
[17179574.176000] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[17179574.176000] Allocate Port Service[pcie00]
[17179574.176000] Allocate Port Service[pcie03]
[17179594.400000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

```

do i have an irq problem? and if so how to i fix it?

thanks!

---

### Post by RMorris78 on 2007-01-17
bump

---

### Post by RMorris78 on 2007-01-23
anyone?

---

