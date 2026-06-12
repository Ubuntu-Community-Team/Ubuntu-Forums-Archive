---
title: "APIC problems and memtest from LiveCD"
date: 2007-12-25
forum: Apple Intel Users
---

### Post by rcoconnell on 2007-12-25
Last night, my macbook (C2D, not Santa Rosa, running OS X Tiger) had a fairly bad crash
(for reasons unknown).* The fan started running full speed (when the machine shouldn't
have been doing much) and woke me up.* The machine no longer boots OS X (I've reset the
PRAM several times), so I decided to try to boot a Gutsy LiveCD (amd64) to see just how
bad things are.* They seem to be, well, bad.* I have several ubuntu questions -- I'm also
going to throw in the little diagnostic data I get from OS X, in the hope that there are
some sharp OS X users here as well!

**Symptom 1:  Trying to boot OS X**

If I boot OS X with command-V, so as to see what's going on, I get the following:

```

hi mem tramps at 0xffe00000
PAE enabled
64 bit mode enabled
standard timeslicing quantum is 10000 us
vm_page_bootstrap: 509086 free pages
mig_table_max_displ = 71
Enabling XMM register save/restore and SSE/SSE2 opcodes
87 prelinked modules
ACPI CA 20060421
AppleIntelCPUPowerManagement: ready
AppleACPICPU: ProcessorApicId=0 LocalApicId=0 Enabled
AppleACPICPU: ProcessorApicId=1 LocalApicId=1 Enabled
Copyright (c) 1982, 1986, 1989, 1991, 1993
         The Regents of the University of California. (c)  All rights reserved.
using 10485 buffer headers and 4096 cluster IO buffer headers
Enabling XMM register save/restore and SSE/SSE2 opcodes
Started CPU 01IOAPIC: Version 0x20 Vectors 64:87
ACPI: System State [S0 S3 S4 S5] (S3)

```

I can't make much sense of this, though it sounds like it's stalling while loading some
power management stuff.

**Symptom 2: Trying to boot Gutsy from the LiveCD**

If I try to boot Gutsy from the LiveCD without fiddling with the F6 options, I get the
"Kernel Loading" dialog, followed by a blank screen with two lines of text at the bottom,
```

Kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000

```
I get the same result if I delete "splash" and add "apic=debug" to the F6 options.

**Symptom 3: Booting Ubuntu! APIC not included.**

I can successfully boot if I add "noapic" to the F6 options.  When I get into GNOME, the
keyboard and trackpad both work poorly -- what I've read indicates that the APIC is
involved in timing, so maybe this is the problem?  Anyway, this brings us to the Ubuntu
questions.

**Question 1:** What is APIC?  What changes when I turn it off?  Is it part of ACPI? 
If it's broken, does this indicate a software/firmware problem, or a hardware problem?

**Question 2:** Is there a way to run a memtest from the LiveCD?  If I try to do this
from the main menu, I get a blank screen (maybe more APIC trouble?).  If I try to do this
from the terminal after booting, I'm told that memtest is not installed, and when I try
to run sudo apt-get install memtester, it fails.

**Question 3:** Is the LiveCD able to do other hardware tests?  Like, say, test the
ACPI system?  My OS X disk is many thousands of miles away, so it would be very handy to
be able to do these diagnostics with Ubuntu.

Many thanks,
ross

---

