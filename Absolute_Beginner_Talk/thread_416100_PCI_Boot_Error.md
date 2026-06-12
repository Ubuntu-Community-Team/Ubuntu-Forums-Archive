---
title: "PCI Boot Error"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by nstannik on 2007-04-20
Hello,

I am somewhat new to Ubuntu (a few months now, and very pleased) and am looking for a little help with an  error is displayed when I boot.


After I hit enter on the GRUB loader for "Ubuntu, kernel 2.6.15-28-386" it will go through the normal routine, but after displaying "Ok, booting the kernel" it displays this in the next line:

[171759571.324000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0


The rest of the boot goes fine, and I haven't noticed any problems inside the OS, although it's been like this since I installed from the Live CD.


I couldn't attach the video of the boot process because of size restrictions but you can get it here:

[http://www.mediafire.com/?dzenwfl4mjz](http://www.mediafire.com/?dzenwfl4mjz)


Please let me know if you need more information, but here is my basic configuration (see signature):

HP Pavilion a1410y
2 GB RAM
3.06 GHz Pentium 4
2 Optical Drives
5in1 Card Reader
Dual Boot with XP
160 GB HD (multiple partitions)
Ubuntu 6.06 Dapper

-----------------------------

I have done my homework:)  and here's what I found so far:

When I run "lspci -v" (as root) here is the first output section:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a33 (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 2a47
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at <ignored> (64-bit, non-prefetchable)


And when I run "dmesg" (also as root), here are a few lines around my problem text:

[17179570.472000] PCI: Using ACPI for IRQ routing
[17179570.472000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.472000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[17179570.480000] pnp: 00:08: ioport range 0xa00-0xa0f has been reserved
[17179570.480000] pnp: 00:08: ioport range 0xa10-0xa1f has been reserved
[17179570.480000] pnp: 00:08: ioport range 0xa20-0xa2f has been reserved
[17179570.480000] pnp: 00:08: ioport range 0xa30-0xa3f has been reserved
[17179570.480000] PCI: Bridge: 0000:00:01.0
[17179570.480000]   IO window: d000-dfff
[17179570.480000]   MEM window: fea00000-feafffff
[17179570.480000]   PREFETCH window: d0000000-dfffffff
[17179570.480000] PCI: Bridge: 0000:00:14.4
[17179570.480000]   IO window: e000-efff
[17179570.480000]   MEM window: feb00000-febfffff
[17179570.480000]   PREFETCH window: disabled.


This post suggests that the problem might be the "double clock speed bug" but none of the symptoms match mine, including the 50% CPU usage and 64bit architecture:

[http://ubuntuforums.org/archive/index.php/t-60487.html](http://ubuntuforums.org/archive/index.php/t-60487.html)


This post has a similar problem, but no offered solution:

[http://www.linuxquestions.org/questions/showthread.php?t=363353](http://www.linuxquestions.org/questions/showthread.php?t=363353)

---------------------------

Thanks in advance for any and all help. I have above average skills on most computers but am still semi-new to Ubuntu and Linux in general, so please keep everything in people terms.

Thanks again,


Nils

---

### Post by zub on 2007-04-21
Hi,

same kind of problem here with a hp pavilion dv6156eu, though it does only appear when I am running feisty with acpi=off in the boot line (and I have to just in order for ubuntu to launch the system).

Could it be a problem in the communication between kernel and ram memory? my two cents

yours
zub

---

### Post by nstannik on 2007-04-21
zub,

Thanks for the reply. Judging by this:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a33 (rev 01)
Subsystem: Hewlett-Packard Company: Unknown device 2a47
Flags: bus master, 66MHz, medium devsel, latency 64
Memory at <ignored> (64-bit, non-prefetchable)

I would hesitate to say that the memory is causing the problem. I'm not that Linux-saavy, though so you may be right. In one of the articles I posted originally, there was something about editing the boot line to remove the error. 

I also don't know what might be changed (if anything) in Feisty. I'll probably be upgrading in a month or so, but I'd like to solve this before then.

Can you give me some hints/tips on changing the boot line (it seems kind of scary to me right now)....

Nils

---

