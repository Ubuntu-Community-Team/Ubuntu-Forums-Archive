---
title: "OK, I'm a real newbie...."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by grover123 on 2007-11-24
Got the .iso, burned it to bootable CD.

Fired up in target system (not this one), and got....

[  132.265559] BIOS bug IO-APIC#1 ID 3 is already used!
[  132.265658] ... fixing up to 1. (Tell your hw vendor)
[  132.307697] MP-BIOS bug: 8254 timer not connected to IO_APIC
Starting system log daemon: syslogd, kiogd.

And then it hangs with a flashing cursor.....

Am I sunk?

Grov

---

### Post by kelbizzle on 2007-11-24
Did you check the cd for defects? I would test that before trying something else if noone else has had this issue. Sometimes burning an image at the fastest speed possible isn't always the most accurate.

---

### Post by grover123 on 2007-11-24
Picked the Check CD option - same result....

Also tried Rescue broken system option - same result; lot of messages, and then hangs at same / screen / result....

---

### Post by kelbizzle on 2007-11-24
> **grover123 said:**
> Picked the Check CD option - same result....

Also tried Rescue broken system option - same result; lot of messages, and then hangs at same / screen / result....

Do you already have it installed? or is this a live cd or what? You may have to pass special options to it. I once had a super old hdd that I swapped for a broken one. I couldn't boot up or even partition but after I told the installer to not use DMA I had no problems.

---

### Post by grover123 on 2007-11-26
I've now tried Ubuntu Live, Ubuntu Alternate, and XUbuntu, all with no success. Disks all verify correctly.


I somehow think it's related to APCI, but can't be sure. If I start install by adding noacpi to command line, it proceeds further, but hangs saying it cannot read from CD.

Perhaps more detail about the environment will help you help me...

Target machine is an older Dual Pentium III, 1 GHz, with 2 SCSI 20 Meg disks, 256 Meg RAM.

Motherboard is ASUS, BIOS is ASUS Medalion v6.0 with P&P extension, Date 08/18/00, Version ASUS CUR-DLS ACPI BIOS Revision 1001

Hard disks are partioned a little strangely (not by me!)
C: 6.83 GB, 2.08 Free
D: 17.0 GB, 16.7 Free
F: 10.2 GB, 10.2 Free

Anything obvious? Is timer needed for CD reads?

Grov

---

### Post by o2deprived on 2007-11-26
I am very new at using Ubuntu (well, Linux in general) but had a similar experience. I can't help you, but I can shed some light (I hope). I used the Ubuntu Live CD (Fiesty & Gutsy) to try it out on my main pc which has an Asus A8N-SLI Deluxe motherboard. It would choke trying to run the CD saying something about an APIC kernal panic error. I even tried the same "-no apic" type command at the start and got the same result, going a little further but the eventual blank screen. My only resolution was to make another pc using the spare parts of older pcs and it runs fine. My guess is you either need to use it on a different pc or see if you can disable the APIC in BIOS.

---

### Post by grover123 on 2007-11-26
Oops - try APIC not APCI! Too early, can't type!

---

### Post by csod64 on 2007-11-26
I'm a "newbie", too.  Was given a live CD last year, worked with my old system perfectly--ecs board with an Intel Pentium 3-compatible AMD processor (please, don't ask me the details--the board's broke and needed to get another one).  My new board is an abit board with an nVida chipset (I think that's what it is...) and an AMD64 Athlon X2 processor (I'm reading that part of the decal.)  The problem when I try to run the regular Live CD--or the one for my system--I get a really weird message about the graphics not being compatible and that I need to get something off the Wikipedia "X" site.  I have absolutely no idea what any of this means.  I'm a hardware geek--have no idea about programming or software.  All I know is build a system and install all the stuff.  (Indicently, I'm running Windows XP Home SP2--hate Vista passionately!)  Can't even run either disk.  Checked both for defects.  None found.  Tried to install the 6.06.1 LTS i386 desktop into a much slower machine, but it seems to be a bit too powerful for it--an Intel Pentium 2 compatible AMD processor (once again, don't ask me the details, please).  Now am installing the file for XUBUNTU  to my desktop so I can burn it into a cd for the slow system--but it's taking forever.  Help!!!!!!!!!!!  SOS!  Please, can someone gently breakdown what I need to do in order to get my regular system to run a live Ubuntu CD--especially what the f* is the Wikipedia X foundation, and how do I get the stuff off of it that I need?  Arrrrrrrrgh!

---

