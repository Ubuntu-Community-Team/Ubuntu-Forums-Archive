---
title: "Newbie Help - Shuttle ST20G5"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Jonathan.Martin on 2006-06-03
Hi,

I am having problems installing Dapper 32/64bit on my shuttle ST20G5 with AMD64 3500+ Manchester core. On standard bios settings I get an timer not connected IO-APIC problem.  I have read on the boards ths can be overcome by using the startup option noapic, which i have done.

The problem is on doing this the Kernal falls over with a sync problem directly after what looks like skipping the apic check. Any info would be greately appreciated.

Also if any 1 can state they have actually installed this on the ST20G5 motherboard it would also be useful, just so I know im not wasting my time ](*,) 

Thank All,

Jonathan.

---

### Post by Jonathan.Martin on 2006-06-03
Ok,

After removing all usb devices from my system and trying loads of differing command line boot combinations still had no joy.  Downloaded the alternate version as suggested in a couple of posts on here and it worked first time no problem at all.

Though I have to admit I havent a clue why the alternate version should work so easily and what the differences are between the two.

Cheers,

Jonathan.

P.S. Dapper looks good.

---

### Post by KimJarvis on 2006-06-16
I used boot parameters 'acpi=off noapic'.

During install got messages: 

Buffer I/O error on device hda, logical block 178656.  

The message came 5 times, took ages, then the live CD boot completed.

I experemented with various settings of the ULi M5287 raid controller.  None of them worked so I currently run with raid on in the Bios but no raid configured.  

With raid 0 configured, and two SATA drives the install completed but initial boot got Error 17 from grub loader.  I looked around on the net but there is not yet a driver for the M5287 raid controller.

---

