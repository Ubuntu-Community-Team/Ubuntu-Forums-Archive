---
title: "Problem with PCI alocation of the resource region. How to fix it?"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by pmilin@ptt.yu on 2006-08-31
I have posted same question to another forum, but none answered. So, I am trying my luck here. I have a problem with getting a following message:
PCI: cannot allocate resource region 7 (also for regions 8 and 9). 
Here is the part of the dmesg, which contains error message:
```
[17179574.684000] PCI: Using ACPI for IRQ routing
[17179574.684000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.684000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179574.684000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179574.684000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179574.796000] PCI: Bridge: 0000:00:01.0
[17179574.796000] PCI: Bridge: 0000:00:1c.0
[17179574.800000] PCI: Bridge: 0000:00:1c.1
```
Is that something related to my graphic-card? Problem with fglrx driver? I really would like to fix that problem, and I even don't know how serious it is.
Please, help me with that. I also noticet quite a lot of messages with the same or similar problem.

Sincerely,
[email]pmilin@ptt.yu[/email]

---

### Post by armware on 2006-10-13
maybe we can figure this out. i get the same errors and have no idea what could be causing it. perhaps we should comare hardware to find the common denominators?

hp pavilion dv8230us
intel core duo T2300 (1.66ghz)
2 sata hdd's
nvidia go 7400

i'd add more hardware info, but i hardly see how ram or screen size could be it, but i suppose if i'm wrong, we'll find out sooner or later.

i notice these messages really early on in the boot process, so it's quite possible that these are just messages from the kernel poking around for hardware to initialize and are nothing out of the ordinary.

---

### Post by sedd on 2006-10-13
I get a similar message, though not quite the same:

[17179576.396000] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0

it happens at the some point in the boot process though, right in between

[17179576.268000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

and 

[17179576.396000] PCI: Bridge: 0000:00:01.0

I have an HP Compaq nw9440. I don't know if it affects anything or not, but my ACPI isn't working quite right. It doesn't get the ac-power connect/disconnect events. Maybe this is related.

---

### Post by firestormx37 on 2008-01-26
I get seven of the PCI: Cannot allocate resource region ........ errors.
In addition, I get one of the PCI: Failed to allocate mem resource #6........ errors.

I would like to fix this because my boot process hangs there for a little before it continues to boot.  

I am using an HP dv5000 with intel core duo T2500, nvidia go 7400.
I am running Gusty Gibbon with all the updates, though I had this problem with Feisty too.

Any ideas about this would be appreciated.

---

