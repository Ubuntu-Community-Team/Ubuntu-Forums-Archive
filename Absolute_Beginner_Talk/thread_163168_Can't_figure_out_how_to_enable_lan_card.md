---
title: "Can't figure out how to enable lan card"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by sullust on 2006-04-20
Hi all,

I can see my lan card when i do a 'lshw -C network':
[FONT="Courier New"]  *-network DISABLED
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 03
       serial: 00:16:36:21:4a:0f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 multicast=yes
       resources: iomemory:b0300000-b031ffff iomemory:b0200000-b02fffff ioport:3000-301f irq:17
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:b0400000-b0400fff irq:17
  *-usb
       description: Bluetooth wireless interface
       product: Acer Module
       vendor: Broadcom Corp
       physical id: 1
       bus info: usb@4:1
       version: 1.00
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s[/FONT]

but when I try to use 'ifconfig eth0 up', i still don't see it in any of the default kde network tools. 

Can anyone let me know what I'm doing wrong or where I should look to see if it's loaded correctly? I tryed 'network-admin' but kubuntu didn't find the executable.

Thanks!
Dave

---

### Post by vigi1 on 2006-04-20
Hi Iam not sure if this will help but I had no trouble configuring. I downloaded an autotool called "Configure network card" through the Apllications-Add program Menu.

---

### Post by notoriouslou1022 on 2006-04-20
hmm

---

