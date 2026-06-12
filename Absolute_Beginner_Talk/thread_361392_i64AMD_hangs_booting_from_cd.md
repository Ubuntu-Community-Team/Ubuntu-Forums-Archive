---
title: "i64AMD hangs booting from cd"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Ubatuba on 2007-02-14
My system information:

Base processor
Athlon 64 X2 (W) 3800+ 2.0 GHz (35W)
      2000 MT/s (mega transfers/second)
      Socket AM2
Chipset
GeForce 6150 LE
Motherboard
      Manufacturer: Asus
       Motherboard Name: A8N-BR
       HP/Compaq motherboard name: Pyrite-GL8E

System Manufacturer	HP Pavilion 061
System Model	RC677AA-ABA s7627c
System Type	X86-based PC
Processor	x86 Family 15 Model 75 Stepping 2 AuthenticAMD ~2004 Mhz
Processor	x86 Family 15 Model 75 Stepping 2 AuthenticAMD ~2004 Mhz
BIOS Version/Date	Phoenix Technologies, LTD  3.05, 11/1/2006
SMBIOS Version	2.4
Windows Directory	C:\WINDOWS
Total Physical Memory	1,024.00 MB

My computer will boot Ubuntu 6.10 from the "i86 cd" and everything works OK

When I try to boot from the "amd64 Version 6.10" cd my computer hangs up.
I preformed the md5sum check and the checksum matched.

The last message to display during the boot process is as follows:
"46.455709 io scheduler CFG Registered(default)"

After this message is displayed I have a blinking cursor at the beggining
of the next line. all disk activity ceases and it appears to hang here.

Thanks for any help!:

---

### Post by DROWE859 on 2007-02-14
The CD may have burned improperly, in that case I would suggest using the "Check CD for Defects" menu option.

---

### Post by Ubatuba on 2007-02-15
The "Check CD for Defects" function from the menu also causes to computer to hang up.

Is there a stand alone version of the "Check CD for defects" software program that will run a checksum against the CD and DVD's I burned. I get the same, or similiar, hang from the CD version as well as the DVD version of Ubuntu 6.10 (2 different disk burned from 2 different files)

I ran a check sum on the files I downloaded and they matched.

Thanks for your reply!

---

### Post by Maestro23 on 2007-02-15
Are you burning the images at a slow speed?  I burned mine at 4X and had no problems.

---

### Post by Ubatuba on 2007-02-16
I tried that yesterday with the same results. The 32 bit version of 6.10 works fine but the amd64 version still hangs. Must be something to do with this Slimline PC's  configuration I guess.

---

### Post by SCAlbano on 2007-05-09
Under more options (f6) on the opening page, try typing in: 

noapic nolapic

as arguements at the end of the default command line.  That is how I was finally able to boot the cd on my new HP box.

---

