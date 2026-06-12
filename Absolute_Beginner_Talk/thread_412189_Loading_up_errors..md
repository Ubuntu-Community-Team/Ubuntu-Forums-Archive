---
title: "Loading up errors."
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Hatchy on 2007-04-17
Hi,
I'm completely new to linux as of last night. 
I installed edgy from CD and had quite a few problems getting it to go, I turned the splash off and found that it was saying to try using 'irqpoll'. So I did. :D 

I can't start the computer now without using irqpoll and the splash off. I've gone through and added all the updates that the updater had. :( 

The errors - 
Something about not finding IRQ # 169 and having to turn it off
Lots and lots of repeating Buffer I/O error. 

Can anyone help?

---

### Post by caffienefree on 2007-04-17
Can you please post the output of: cat /proc/interrupts

---

### Post by Hatchy on 2007-04-18
Ok - 
The i/o error is on device - sda2 logical block 0
The irq 169 message is :nobody cared.

          CPU0       CPU1       
  0:     242151          0    IO-APIC-edge  timer
  7:          0                 0    IO-APIC-edge  parport0
  8:          3                 0    IO-APIC-edge  rtc
  9:          1                 0   IO-APIC-level  acpi
169:     300216        0   IO-APIC-level  ide0, ide1, libata, uhci_hcd:usb3
177:     125906        0   IO-APIC-level  uhci_hcd:usb1, uhci_hcd:usb4, nvidia
185:          0               0   IO-APIC-level  uhci_hcd:usb2
193:          2               0   IO-APIC-level  ehci_hcd:usb5
209:          0               0   IO-APIC-level  eth1
217:       2327           0   IO-APIC-level  skge
225:       1232           0   IO-APIC-level  Intel ICH5
NMI:          0               0 
LOC:     241982     241981 
ERR:          2
MIS:         17

---

