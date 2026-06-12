---
title: "ACPI: Unable to locate RSDP"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by cde on 2007-07-07
I've been battling this problem for a couple days now. I have a Pentium II machine with 256MB of Ram and I deleted the partition (that held Windows 98 SE) to make a clean install of Xubuntu 7.04. I've tested the disk on other machines to verify that the CD works.

When using the Xubuntu Live CD, I never reach the standard menu screen. Instead I get a screen with the Xubuntu banner and the following text:

This is the Xubuntu Live CD.
Press F1 for help and advanced options.

For the default live system, press ENTER:

Boot: _

After pressing enter I get a screen that reads "ACPI: Unable to locate RSDP" and than it hangs on an entirely black screen.

memtest passes all 8 tests.

Xubuntu is able to install from the Alternate CD but at both beginning and end I get "ACPI: Unable to locate RSDP."

On reboot it loads the Grub, gives the screen "ACPI: Unable to locate RSDP" and then hangs on black screen.

When turning on ACPI Aware O/S from the Power Management settings in my Bios, the error message is replaced with "BIOS age (1999) fails cutoff (2000) acpi=force is required to enable ACPI" but is still followed by a black screen.

My Bios is AMIBIOUS EASY SETUP UTILITY Ver. 1.16

I'm able to press ESC when Grub is loading. 

Is there anything I can do? Any responses appreciated. Please dumb down instructions for me if you can.

---

### Post by oilchangeguy on 2007-07-07
with a pent 2 (you don't say the cpu's speed) i'd suggest you use xubuntu 6.06. and if the bios fails the 2000 cutoff, try damn small linux.

---

### Post by cde on 2007-07-07
Alright, I'll try 6.06 and I've already tried DSL but the display was TERRIBLE. Could hardly read anything.

---

### Post by oilchangeguy on 2007-07-07
> **cde said:**
> Alright, I'll try 6.06 and I've already tried DSL but the display was TERRIBLE. Could hardly read anything.

not ubuntu 6.06, xubuntu 6.06.

---

### Post by cde on 2007-07-07
Yeah, I actually already tried Ubuntu 6.06 and it didn't work. I'm downloading Xubuntu 6.06 Alternate CD.

---

### Post by cde on 2007-07-07
One thing though. I noticed Ubuntu 7.04 could detect and install my NIC on another computer but 6.06 couldn't... I was worried I'd run into problems with manually installing my NIC's driver on Xubuntu 6.06.

---

### Post by deepclutch on 2007-07-07
the problem is ur bios is a lil old(ur pc too :p ).that time apm may be the norm.so while ur grub menu shows press "e" and in the " kernel" line append **acpi=off apm=on**   press enter,press **b** and see whether it works.

---

### Post by oilchangeguy on 2007-07-07
> **cde said:**
> One thing though. I noticed Ubuntu 7.04 could detect and install my NIC on another computer but 6.06 couldn't... I was worried I'd run into problems with manually installing my NIC's driver on Xubuntu 6.06.

most nic's work out of the box. ubuntu/linux's problem usually is with internal modem's.

---

### Post by cde on 2007-07-07
> **deepclutch said:**
> the problem is ur bios is a lil old(ur pc too :p ).that time apm may be the norm.so while ur grub menu shows press "e" and in the " kernel" line append **acpi=off apm=on**   press enter,press **b** and see whether it works.

Lemme see if I understand what you're saying. Edit the kernel line so the end has apci=off apm =on?

---

### Post by cde on 2007-07-07
Nope, doesn't work. Running installation for Xubuntu 6.06 Alternate CD now.

---

### Post by cde on 2007-07-07
Same thing with Xubuntu 6.06 :(

---

### Post by deepclutch on 2007-07-08
hrmm.. 
but u can try as per the error suggest as of OP.edit the kernel line and prepend "acpi=force" only without the quote.
if that too fails and u cant boot.try "acpi=off" alone.
"pci=noacpi" is another try if "acpi=off" not work.
another tries are:
" irqfixup " be added to kernel line.
noapic nolapic lines too can be tried.

---

