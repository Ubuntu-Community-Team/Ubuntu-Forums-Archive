---
title: "looking for &quot;irq10&quot; answers"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by YoungPastor on 2007-11-28
I'm having the problem of a spammed "serial8250: too much work for irq10" and while I've read many other posts about this problem across many other forums, I've yet to find an answer. What does this mean?!

Oh, and for some reason, my 512 MB RAM system only reads as having 447 MB. It reads this in the BIOS before booting and in the sys monitor after booting, whether in ubuntu or XP. I tried the RAM in another laptop, and it reads 512, so it appears the RAM itself is fine. What imformation do you, community, have about this problem? Thanks for all your help

---

### Post by YoungPastor on 2007-11-28
still no solution for home to offset the load on irq10 or what load that is, but I found this piece of info on wikipedia if anyone else finds this thread looking for help rather than offering it. (all of the below is quoted from wikipedia.org)


The PC/XT ISA system had one 8259 controller, while PC/AT and later systems had two 8259 controllers, master and slave. IRQ0 through IRQ7 are the master 8259's interrupt lines, while IRQ8 through IRQ15 are the slave 8259's interrupt lines. The actual names on the pins on an 8259 are IR0 through IR7. IRQ0 through IRQ15 are the names of the ISA bus's lines to which the 8259's are historically attached.

Master 8259 
IRQ0 – Intel 8253 or Intel 8254 Programmable Interval Timer, aka the system timer 
IRQ1 – Intel 8042 keyboard controller 
IRQ2 – not assigned in PC/XT; cascaded to slave 8259 INT line in PC/AT 
IRQ3 – 8250 UART serial port COM2 and COM4 
IRQ4 – 8250 UART serial port COM1 and COM3 
IRQ5 – hard disk controller in PC/XT; Intel 8255 parallel port LPT2 in PC/AT 
IRQ6 – Intel 82072A floppy disk controller 
IRQ7 – Intel 8255 parallel port LPT1 / spurious interrupt 

Slave 8259 (PC/AT and later only) 
IRQ8 – real-time clock (RTC) 
IRQ9 – no common assignment 
IRQ10 – no common assignment 
IRQ11 – no common assignment 
IRQ12 – Intel 8042 PS/2 mouse controller 
IRQ13 – math coprocessor 
IRQ14 – hard disk controller 1 
IRQ15 – hard disk controller 2 
Initially IRQ7 was a common choice for the use of a sound card, but later IRQ5 was used when it was found that IRQ7 would interfere with the printer port (LPT1). The serial ports are frequently disabled to free an IRQ line for another device.

IRQ2/9 is the traditional interrupt line for a MPU-401 MIDI port, but this conflicts with the ACPI system control interrupt (SCI is hardwired to IRQ9); this means ISA MPU-401 cards with a hardwired IRQ 2/9, and MPU-401 device drivers with a hardcoded IRQ 2/9, cannot be used in interrupt-driven mode on a system with ACPI enabled.

---

### Post by YoungPastor on 2007-11-28
I've finished understanding it: the irq10 problem went away when I tried installing ubuntu 7.10 proper, rather than a distro based on it (gOS). So, it might have been nice to learn more about irq10, but the problem seems to be gOS related, not ubuntu related. I thought gOS was so close to ubuntu that it wouldn't have changed anything fundamental.

The RAM situation is that this old compaq Presario 2100 lappy/paperweight I'm using shares its memory for video, so I can set the BIOS to allocate more or less ram to video, and the remaining is what shows up as available for the system. 

Thanks, me.

---

