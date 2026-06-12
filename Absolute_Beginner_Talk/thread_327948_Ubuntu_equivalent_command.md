---
title: "Ubuntu equivalent command"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-12-30
I need the following type of information about my modem.

Bus 0. device 12, function 0:
       Communication controller: Lucent (ex-AT&T)
       Microelectronics Unknown device (rev 0).
       Vendor id=11c1. Device id=480.
       Medium devsel. Fast back-to-back capable. IRQ 11. Master capable. No bursts. Min Gnt=252.Max Lat=14.
            Non-prefetchable 32 bit memory at 0xe0800000 [0xe0800000].
            I/O at 0xa000[0xa001].
            I/O at 0x9800 [0x9801].
            I/O at 0x9400 [0x9401].

The post I found the above in used:

cat /proc/pci

this isn't the Ubuntu command, please tell me the equivalent command. Thnx.

---

### Post by sardion on 2006-12-30
I think you want

lspci

but I am not with my box right now so I can't check that.

---

### Post by Mark_in_Hollywood on 2006-12-30
No, not

lspci

I tried that one, too.

---

### Post by sardion on 2006-12-30
Hmm...

As I said I am not near my box right now, but I think I got my modem set up using the scripts supplied with the slmodem daemon (which is in multiverse).

Look into that (either by installing via multiverse or by googling slmodem).  I know somewhere in that package is a script that probes modems and tells you all that.

Hope you get this figured out.

---

