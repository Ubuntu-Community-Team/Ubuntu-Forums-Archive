---
title: "Question about interrupts"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by pnix on 2007-05-21
I try to manage nvidia driver to work on my system and found that I must pass acpi=off and irqpoll to kernel to make X can start(if not I'll get black screen and Xorg.0.log complain about nvidia module not receive interrupt)

Anyway with those two parameters, System and X start ok. But I have a question when I try 
cat /proc/interrupts
I get
          CPU0      
  0:      18977    XT-PIC-XT        timer
  1:         69    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:        532    XT-PIC-XT        NVidia nForce2
  5:         74    XT-PIC-XT        eth0, ohci_hcd:usb3
  6:          5    XT-PIC-XT        floppy
  7:     100030    XT-PIC-XT        ohci_hcd:usb1, nvidia
  8:          3    XT-PIC-XT        rtc
  9:          3    XT-PIC-XT        ohci1394
 10:          0    XT-PIC-XT        MPU401 UART
 11:       6229    XT-PIC-XT        ehci_hcd:usb2, libata
 12:       1088    XT-PIC-XT        i8042
 14:        116    XT-PIC-XT        ide0
 15:        269    XT-PIC-XT        ide1
NMI:        354
LOC:      18861
ERR:         53
MIS:          0

Is thist OK? what ERR mean? It look like nvidia share interrupts with usb but both still work fine??

---

### Post by Cypher on 2007-05-21
This is completely fine. The need for exclusive interrrupts lines (IRQ) died, thankfully, with the ISA and older architectures. All new system hardware and drivers/OS support for sharing of a single line across many devices without any issues.

So you shouldn't worry about it..

---

### Post by pnix on 2007-05-21
Thanks Cypher, that ERR make me worry about performance.:D

---

