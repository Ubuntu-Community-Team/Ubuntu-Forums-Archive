---
title: "Ubuntu  on strike"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Heathcliff on 2008-02-27
Damn thing up and quit on me. Help. 

I had Ubuntu 7.10 Gutsy Gibbon running smoothly, then one day it just started freezing on load, right after "Starting up..." 

Tried reinstalling from the live and alternate CD, but get the same blank screen right after the "Loading Linux Kernel" progress bar reaches its endpoint.

Unable to boot from Supergrub.

If I select Recovery mode from the GRUB menu, I get a couple pages of stuff before the computer freeze that ends with: [ 12.9388447 ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11

Does that mean I have an interrupt conflict? 

My system. IBM Stinkpad A21m, 512 megabytes RAM, 40G hard drive, dual boot Windows 2000 Pro/Ubuntu 7.10. The only significant change I made since Ubuntu last worked was sticking in my wireless PCMCIA card. Could that crash the system? Removing it doesn't help.

---

### Post by Arthur Archnix on 2008-02-27
Some ideas:

1. Boot the live cd and do a memory check
2. Look for a bios upgrade
3. Find a disk health checker from your computer manufacturer and run it.
4. Completely erase your HD using dban, simple overwrite (fill with zeros), and try again.
5. Still no good? Wow. Ok, try adding noacpi as a boot option.

That's it. I'm out of ideas. Good luck.

---

### Post by OffAxis on 2008-02-27
does your windows 2000 start normally?
with and without the pcmcia card in?

---

### Post by Arthur Archnix on 2008-02-27
Huh.. sorry about that. Missed the dual boot reference.

---

### Post by Mwelsh on 2008-02-27
I would try disabling the ACPI controller in your BIOS before baking your hard drive. 

Otherwise, I'd agree with Archnix

---

### Post by Heathcliff on 2008-02-27
> **Arthur Archnix said:**
> Some ideas:

1. Boot the live cd and do a memory check
2. Look for a bios upgrade
3. Find a disk health checker from your computer manufacturer and run it.
4. Completely erase your HD using dban, simple overwrite (fill with zeros), and try again.
5. Still no good? Wow. Ok, try adding noacpi as a boot option.

That's it. I'm out of ideas. Good luck.

1. Live CD doesn't boot.
2. Worked perfectly for awhile.  I added all available Lenovo system updates.
3. Hard drive is almost brand new since I bought the laptop as a reconditioned IBM item and the drive was replaced under the warrantee.
4. Wow.
5. I think I tried that using SystemRescueCd from SourceForge.net
---------------------------

 	
Re: Ubuntu on strike
I would try disabling the ACPI controller in your BIOS before baking your hard drive. 

I'll see if I can figure that out. Then again, Windows still works. What does the ACPI controller do?

---

### Post by chris.a.barker on 2008-02-27
ACPI controller controls things like sleep and standby...

---

### Post by Arthur Archnix on 2008-02-28
> Tried reinstalling from the live and alternate CD, but get the same blank screen right after the "Loading Linux Kernel" progress bar reaches its endpoint.

Then...

> 1. Live CD doesn't boot.

Describe exactly what happens. You can obviously boot the cd, since it begins to read from it, then fails at some point. With the live cd does it fail before you get to the menu that says "start/install ubuntu", because that's where the memory test is located.

Did those updates include a bios update? If so, did it fail or give any errors? Did you unplug the laptop at all while it was updating or did the power go out? Have you tried resetting the bios to defaults?

Also, also, do you get to the grub screen? If so, highlight Ubuntu, press 'e', go to the kernel line, press 'e', go to the end of the line and add 'noapic', without quotes, press enter, then 'b'.

---

### Post by warrior24 on 2008-02-28
try taking a stick of ram out assuming that you have two stick. Or try a stick you may have lying around.

---

