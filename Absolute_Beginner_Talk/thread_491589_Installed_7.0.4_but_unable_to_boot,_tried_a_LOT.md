---
title: "Installed 7.0.4 but unable to boot, tried a LOT"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by domyalex on 2007-07-03
Hi to all!
I have unsuccessfully trying to install/boot Ubuntu 7.0.4 for 3 days now on my desktop.
First of all I am kind of newbie when it comes to Linux, but have fair knowledge of computers and Windows.
Anyway, I downloaded/burnt the LiveCD and on my wife's Toshiba Satellite it boots perfectly (writing this from her notebook).
I checked the MD5 checksum, it's fine
I checked my desktop memory from the CD utility and it didn't find any errors.

My desktop:
P4 2.4Ghz
Motherboard PcChips M909 V5.0A
Chipset Intel i845E/G/PE/GE
512 RAM
2 HD
GPU: GeForce 6200 AGP PRO

There was no way I could boot from the LIveCD, so I got the Alternate CD and was able to install it on a partition of its own, however it will not boot (dualbooting with Win XP Pro; Win still boots fine).
I searched around this forums and tried a *lot* of parameters, here are my errors:

[LIST]
[*]**normal boot**: native_apic_write_atomic+0x6/0x10
[*]**recovery mode**: native_apic_write_atomic+0x6/0x10

[*]**noapic nolapic**: error_code+0x7c/0x90
[*]**noapic acpi=noirq**: says something about sysfs bridge and then starts displaying a lot of messages (too fast to read)
[*]**noapic acpi=off**: lots of messages
[*]**noapictimer**: IOAPIC invalid reference to IRQ 0 and then failed to set xfermode (err_mask=0x40)
[*]**noapictimer irqpoll**: IOAPIC invalid reference to IRQ 0 and then unable to handle kernel paging request at virtual address 030c2444
[/LIST]

Similars errors (native_apic_write_atomic+0x6/0x10 or error_code+0x7c/0x90) resulted from the following parameters being used:

[LIST]
[*]**noapic nolapic irqpoll**
[*]**apic=off irqpoll**
[*]**noapic**
[*]**pci=routeirq**
[*]**irqpoll**
[*]**acpi=off**
[*]**ide=dma**
[*]**irqpoll pci=noacpi noapic nolapic acpi=off**
[/LIST]

Any ideas? I'm really running out of options here...  :(

Regards

---

### Post by rickycodie on 2007-07-03
i believe that it might be a restricted video driver, does the x server fail? or do you even get there?

---

### Post by bradmayne on 2007-07-03
Is there any way you could try using an older version such as edgy or dapper?  I've had problems that are similar I am writing this on a toshiba satellite a135 s4527.  However I have tried to install knoppix on this pc and knoppix would not boot on my toshiba (which is brand new) but workd fine on an old e-machine.  Try it out if you can and let me know!!

---

### Post by domyalex on 2007-07-04
I never get past the splash screen, so I don't think X is loading...

Just in case, I tried a PCLinux 2007 LiveCD with similar results; after I got to Detecting video cards I got the long, too fast to read, list of messages.
I tried the same CD on my workstation at work (Dell 3.0 HT and PCLinux booted just fine, so it must be something with my desktop hardware configuration...

I remember that I was able to boot Knoppix like 2 years ago, but haven't tried again...
Oh well, I'll try edgy or drapper and will let you know

Thanks for your time, I apreciate it!

Regards

---

### Post by domyalex on 2007-07-04
Solved the problem!
It was due to some weird behavior of the PCChips motherboard and the AGP drivers; thanks to the guys from [www.notebookreview.com](www.notebookreview.com), I was sent to [this]("http://doc.gwos.org/index.php/Nvidia_Intel_Integrated") site, followed the instructions and all went well!

Hope it helps somebody in my same situation

Regards

---

### Post by rickycodie on 2007-07-05
great i'm glad you solved it!

---

### Post by Vadi on 2007-12-23
That link is no longer active.

Do you remember how did you solve the issue?

---

