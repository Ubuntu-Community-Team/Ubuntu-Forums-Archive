---
title: "WVDial reports cannot set information for serial port"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-08-14
Clicking "Check If Already Posted" returned: Sorry - no matches. Please try some different terms. I tried.

Why does wvdial conf not properly set the serial port? How and where does setserial enter into this to fix the problem. I can't find the files that "man setserial" says exist for debian (ubuntu). I tried resetting the BIOS from

I/O address of 3F8 to 2F8
and the INT from IRQ 4 to IRQ 3

but that didn't help. 

Below is the wvdial log:

mark@Lexington:~$ wvdial
--> WvDial: Internet dialer version 1.55
**--> Cannot set information for serial port.** [bold by me]
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDTXXXXXXX
--> Waiting for carrier.
ATDTXXXXXXX

---

