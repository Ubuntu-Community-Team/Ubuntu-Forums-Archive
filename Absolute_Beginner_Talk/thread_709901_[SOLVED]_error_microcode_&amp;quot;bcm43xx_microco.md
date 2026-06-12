---
title: "[SOLVED] error: microcode &amp;quot;bcm43xx_microcode5.fw&amp;quot;?????"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by capozziatc on 2008-02-27
ok im a complete noob to Linux entirely and I could really use some help.  i have a dell inspiron 1520 laptop and i decided i wanted to learn how to use Linux because i work at a pc repair shop and i figured it be useful to know something about unix based systems.

ok so hears my problem i downloaded Ubuntu gutsy and burnt it to a disk and installed it.  but after completing the install when Ubuntu goes to load for the first time i get this "error: microcode "bcm43xx_microcode5.fw"" and it just slowly repeats itself as if its going know where.  so i googled it.  i found a bunch of different answers. something about drivers and firmware for my "Broadcom wireless chipset".  But in almost all of them the solution required me to go into terminal and input commands, or load a driver.  

first off i cant get the system to boot so i don't know how else i could get to terminal.
secondly im a total noob and i wouldn't know a way to go into a "safe" or "protected" mode to do this either.

so i guess what im really asking is for a step-by step process on how to resolve this issue

P.S wasnt sure if this was an issue but i have a core 2 duo Processor, which has 64 bit capabilities.  so i used the "64bit AMD and Intel" version.  seeing the word Intel i figured qualified for that iso.  not sure if this could actually be a problem, but i dont think so.

---

### Post by spiderbatdad on 2008-02-27
You should have several seconds just before the boot process in which to press the esc key. This will bring up the grub options. Recovery boot is there. Also F1, I believe, will give you a command line. You should be able to edit the kernel parameters from thats screen as well, if that is your plan. Are you trying acpi=off?

---

### Post by capozziatc on 2008-02-27
actually its alright i think i figured it out.  what i believe happened was when i originally set it up i told it to use the wireless card as the "default" network device.  this time i skipped all that by loading the "live interface" and installed it through there.  and know it works perfectly, in fact as i speak its browsing the internet, and downloading updates.  my only issue know is that dell doesn't offer and chipset drivers for Linux. :-/  so know i have no sound.  i believe i can get those drivers by downloading the base driver for the chipset i just don't quite remember who makes it.... probably Intel.  which means ill probably be back.

---

### Post by igknighted on 2008-02-27
You just need to install the firmware for the broadcom device.  Restricted driver manager should do this for you.  Just ignore any error messages that flash up on booting the live cd.

---

