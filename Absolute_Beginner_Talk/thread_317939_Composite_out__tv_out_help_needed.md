---
title: "Composite out / tv out help needed"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Ashrael on 2006-12-13
I can't seem to get my tv out working on my laptop (compaq armada m700) 

TRIED A LOT, but this is my last attempt to figure it out...

 $:/usr/X11R6/bin# get-edid | parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 200
        VBE string at 0x11110 "ATI MACH64"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination does not support DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call failed

The EDID data should not be trusted as the VBE call failed
EDID claims 19 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).

        # EDID version 19 revision 19
Section "Monitor"
        Identifier "DXS:1313"
        VendorName "DXS"
        ModelName "DXS:1313"
        # DPMS capabilities: Active off:no  Suspend:no  Standby:no

        Mode    "275x275"       # vfreq 43.295Hz, hfreq 45.979kHz
                DotClock        48.830000
                HTimings        275 294 313 1062
                VTimings        275 276 327 1062
        EndMode
        Mode    "275x275"       # vfreq 43.295Hz, hfreq 45.979kHz
                DotClock        48.830000
                HTimings        275 294 313 1062
                VTimings        275 276 327 1062
        EndMode
        Mode    "275x275"       # vfreq 43.295Hz, hfreq 45.979kHz
                DotClock        48.830000
                HTimings        275 294 313 1062
                VTimings        275 276 327 1062
        EndMode
        Mode    "275x275"       # vfreq 43.295Hz, hfreq 45.979kHz
                DotClock        48.830000
                HTimings        275 294 313 1062
                VTimings        275 276 327 1062
        EndMode
EndSection

ANYBODY any pointers, ideas etc...

---

### Post by daller on 2006-12-13
Sorry if you already posted this, but I hate long posts... :D

What card is it?

---

### Post by Ashrael on 2006-12-14
Well it says it's an ati mach 64...In a compaq armada M700.
Any ideas are welcome..

---

### Post by daller on 2006-12-14
I know it isn't the same model, but it looks like a generic ati solution...

[https://wiki.ubuntu.com/Radeon7500TVOut](https://wiki.ubuntu.com/Radeon7500TVOut)

---

