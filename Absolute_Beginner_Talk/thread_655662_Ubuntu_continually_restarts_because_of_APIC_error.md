---
title: "Ubuntu continually restarts because of APIC error"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-01-01
My 64-bit Ubuntu 7.10 keeps on rebooting while trying to load on startup. This problem exists for everything: trying to start Ubuntu via the Live-CD, via hard drive, via recovery mode

I've checked the threads on these forums and have tried what people have suggested with little success:
> 1. appending noapic nolapic nosplash to boot sequence (strange thing is this has worked a couple of times out of 50+ restarts, I managed to boot into the Live-CD with this method and I was able to install Ubuntu)
2. updating my BIOS
3. appending noapic nolapic
4. appending noapic
5. acpi=off
6. acpi=ht


My relevant computer specs:
> 64bit Ubuntu 7.10, Gigabyte P35-DS3L (with latest BIOS), Q6600, GeForce 8400GS, LSI 21320 SCSI hba, 2x Hitachi 15k300 Ultrastar hard drives.

During bootup I'm getting:
> Inquiring remote APIC #2...
... APIC #2 ID: failed
... APIC #2 VERSION: failed
... APIC #2 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 2/3 APIC 0x1
Not responding.

Inquiring remote APIC #3...
... APIC #3 ID: failed
... APIC #3 VERSION: failed
... APIC #3 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.

Inquiring remote APIC #1...
... APIC #1 ID: failed
... APIC #1 VERSION: failed
... APIC #1 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.


Does anyone know how to remedy this problem -- it's so frustrating :(? Do I have to change some motherboard setting? Why does the noapic nolapic work only sometimes? What's wrong with my APIC? 

Thank you very much for the help

---

### Post by HermanAB on 2008-01-01
Hmm, I'm sorry, but you really should try a different distribution: Mandriva, Fedora or Suse comes to mind.  If it works better with another distro, either stick with that, or use it to figure out what is the matter with your hardware support.

The simple fact of the matter is that all distros don't work with all hardware - shop around.

Cheers,

H.

---

### Post by dcstar on 2008-01-01
> **inktri said:**
> My 64-bit Ubuntu 7.10 keeps on rebooting while trying to load on startup. This problem exists for everything: trying to start Ubuntu via the Live-CD, via hard drive, via recovery mode
........
Does anyone know how to remedy this problem -- it's so frustrating :(? Do I have to change some motherboard setting? Why does the noapic nolapic work only sometimes? What's wrong with my APIC? 

Thank you very much for the help

Download the 32bit Live CD and try that, it may behave better.

---

### Post by inktri on 2008-01-01
32-bit works, but i'd like to use 64-bit ubuntu if that's possible

---

### Post by inktri on 2008-01-04
i figured it out finally! :)

just in case someone suffers from the same problem:

my solution was to disable "Enable USB mouse/keyboard" from my motherboard bios

---

