---
title: "Weirdness"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by ALSW123 on 2007-10-30
Hi, I am sorry that my first post is a question but i figure this is as gooder place to ask as any. 

Basically a few months back my laptop had a good old fashioned lock up and subsequently refused point blank to boot or reinstall windows (i know i know it sucks but i use alot of CAD etc) The only way i could get it running was to install Linux, the only distribution I could get to work was Slackware, but I decided it was rather complicated for me! 

Anyway after a few hours of trying today I managed to get the text based install of Ubuntu to install and boot, the regular CD would fail as did many other distros. To get it to boot I had to turn ACPI off in the boot loader, thanks to these forums for that :D I was tearing my hair out but turns out it was that. 

Now ubuntu is all shiny and nice, I'm definitely keeping it for day to day use! Also i'll give emulation a try for my windows applications but does anyone know if ACPI could be why Windows (and many linux distro's) refuses to install? I don't fully comprehend what it is and why it should course such lockups across the board? 

BTW Its an Fujitsu Siemens Amilo a 1630 (amd 64 3700+) 

Thanks again to this wonderful forums archive for helping me to get Ubuntu running!! :D

---

### Post by kingpoiuy on 2007-10-30
ACPI basically gives your OS the ability to control the power management of your system.  Out side of that I don't know why that would affect the install.

[http://en.wikipedia.org/wiki/Acpi]("http://en.wikipedia.org/wiki/Acpi")

---

### Post by amtnbiker16 on 2007-10-30
i dont know anything about acpi, but i have had some degree of luck getting windows apps to work in wine

wine runs windows apps without actually booting windows, so you wont need to install windows to run their applications, this is also a lot faster than running the os (assuming the application cooperates)
you can find wine under add/remove applications

i'd give it a try if i were you, you will have to use the command line a little for install, but its pretty straightforward

---

### Post by ALSW123 on 2007-10-30
> **kingpoiuy said:**
> ACPI basically gives your OS the ability to control the power management of your system.  Out side of that I don't know why that would affect the install.

[http://en.wikipedia.org/wiki/Acpi]("http://en.wikipedia.org/wiki/Acpi")

Thanks, i'll see what i can find out, seems odd to me that something like that would mess everything up suddenly! 

> **amtnbiker16 said:**
> i dont know anything about acpi, but i have had some degree of luck getting windows apps to work in wine

wine runs windows apps without actually booting windows, so you wont need to install windows to run their applications, this is also a lot faster than running the os (assuming the application cooperates)
you can find wine under add/remove applications

i'd give it a try if i were you, you will have to use the command line a little for install, but its pretty straightforward

cheers, i coudl never get it to run under slackware, i'll give it a try, i always assumed it would be dead slow, I'll give em a try :-) Its not my main computer now but it would be useful to have a system that runs the more basic programs we use in school :-)

---

### Post by sailor2001 on 2007-10-30
# 3 ACPI Tables

    * 3.1 RSDP (Root System Description Pointer)
    * 3.2 RSDT (Root System Description Table)
    * 3.3 DSDT (Differentiated System Description Table)
    * 3.4 XSDT (Extended System Description Table)
    * 3.5 FADT (Fixed ACPI Description Table)
    * 3.6 FACS (Firmware ACPI Control Structure)
    * 3.7 SBST (Smart Battery Table)
    * 3.8 ECDT (Embedded Controller Boot Resources Table)
    * 3.9 MADT (Multiple APIC Description Table)
    * 3.10 SRAT (System Resource Affinity Table)
    * 3.11 SLIT (System Locality Distance Information Table)
    * 3.12 SLIC (Software Licensing Description Table)
    * 3.13 SSDT (Secondary System Descriptor Table)

---

