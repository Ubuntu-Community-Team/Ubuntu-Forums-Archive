---
title: "[SOLVED] Problem with the Live CD (different thab any other thread)"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by mitar on 2008-01-20
I have a problem installing Live CD. After booting Ubuntu CD, from the menu I pick "Start or Install Ubuntu". After that i get black screen with a message:

[FONT="Courier New"]Uncompressing Linux... Ok, booting the kernel.
[some number]  MP- BIOS bug: 8254 timer not connected to IO- APIC
[the same number as above] Kernel Panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send report. Then try booting with the 'noapic' option[/FONT]

I have hp pavilion with Vista installed, Nvidia graphics, AMD Turion64, 2Gib of ram...

---

### Post by Mud.Knee.Havoc on 2008-01-20
So did you try booting it with the noapic option?
I've got a Dell Inspiron 1501 that usually will boot into a black screen if I don't boot it with noapic and acpi=off.

---

### Post by mitar on 2008-01-20
:-) I don't know what's that and how to do it

---

### Post by erfahren on 2008-01-20
I'm not sure, but just a suggestion... check the HP site (support > drivers and downloads) and see if there is an update for your BIOS

---

### Post by Desperate on 2008-01-20
Noob here, but I like reading :)
Try starting in the next one "graphics" mode and you'll get in, then check system-administration- screen and graphics (once you're online) and look for the right driver as you're now running a Vesa solution (one solution fits all :) ) If you manage to reinstall your driver then go for install on hard disk.

---

### Post by erfahren on 2008-01-20
I found [this thread](http://www.linuxquestions.org/questions/linux-software-2/kernel-panic-not-syncing-attempted-to-kill-init-313273/) at linuxforums.org where it suggests that the problem my be bad memory.

It sounds like a newer computer, but boot into the CD and run memtest86

---

### Post by jeffus_il on 2008-01-20
> **erfahren said:**
> I'm not sure, but just a suggestion... check the HP site (support > drivers and downloads) and see if there is an update for your BIOS
Soon after you turn the machine on, you get a menu called the grub menu, this is the stage where you choose the linux kernel to load, when you get this menu type "e" to edit the boot command, then go to the end of the line, add noapic, type enter, type "b" for boot. Good Luck!

---

### Post by erfahren on 2008-01-20
> **jeffus_il said:**
> Soon after you turn the machine on, you get a menu called the grub menu, this is the stage where you choose the linux kernel to load, when you get this menu type "e" to edit the boot command, then go to the end of the line, add noapic, type enter, type "b" for boot. Good Luck!
Why are you quoting me? 

The OP is using a LveCD - there'll be no GRUB menu

---

### Post by mitar on 2008-01-20
I really have no idea what all theses people are saying. It looks like I will have to find someone and ask him to install it for me. I am very bad in fixing things on PC

---

### Post by erfahren on 2008-01-20
mitar -- maybe we can just start over

Mud.Knee.Havoc had the right idea - see: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

when your at the LiveCD menu press F6 - you can then enter the boot options - enter "noapic" at the end of the Boot Options line

---

