---
title: "How can I keep logs of the messages displayed during boot (even when Ubuntu fails)?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-01-03
I have this strange start up bug, my machine will get past the boot loader and then restart. Eventually after 20-30 restarts it will eventually load Ubuntu successfully. 

Further inspection by removing the "quiet" flag from the kernel boot command indicates that the error has something to do with APIC... whenever Ubuntu is about to restart my computer it shows APIC failed... something along the lines of:

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


I can't quite catch everything that's flashed on the screen before the restart, so I must ask: is there a way to see the stuff that's written to the screen during boot up? Is it logged somewhere?

Oh and yea I"ve tried a billion different combinations of noapic, nolapic, acpi=off, etc. but none of them seem to fix my problem; Ubuntu appears to load succesfully randomly

Thanks for the help

---

### Post by ~LoKe on 2008-01-03
I believe typing "dmesg" into the terminal would display the information you're looking for.

---

### Post by inktri on 2008-01-03
hey thanks for the fast reply

does dmesg show the boot up log of the last successful login? 

i need the boot up log of the last unsuccessful login (when Ubuntu restarts)

---

### Post by ~LoKe on 2008-01-03
> **inktri said:**
> hey thanks for the fast reply

does dmesg show the boot up log of the last successful login? 

i need the boot up log of the last unsuccessful login (when Ubuntu restarts)

Damn, good point.  Hold on let me see if the logs for previous boots are located anywhere.

---

### Post by ~LoKe on 2008-01-03
```
cat /var/log/dmesg.0
```
I think that's it?  That should be the previous boot.

---

### Post by inktri on 2008-01-03
i just checked, unfortnately those dmesg files are logs only for successful boot ups

---

### Post by ~LoKe on 2008-01-03
> **inktri said:**
> i just checked, unfortnately those dmesg files are logs only for successful boot ups

Have a look around /var/log and see if there's anything there (kern.log, debug.log, etc).

---

