---
title: "[SOLVED] How do you get g4 powerbook to boot from external cd drive?"
date: 2008-07-22
forum: Apple Hardware Users
---

### Post by worx101 on 2008-07-22
I have a firewire external dvd/cd drive as the internal drive is mostly faulty.(unreliable)

I hold opt at boot for the boot menu, I select the boot cd and then it reads the cd and will loop back to the boot menu.

Holding C doesn't work.... and I have tried the opt-cmd-shift-del but it doesn't seem to work either?  maybe I am using the wrong key combo or pressing at wrong time.(not too good with macs, this one was given to me after HDD drive failed and I decided to take a crack at it with linux)

---

### Post by stream303 on 2008-07-22
Check out this solution in the archives:

[http://ubuntuforums.org/showthread.php?t=698290](http://ubuntuforums.org/showthread.php?t=698290)

Basically with the cd in the drive, you boot into openfirmware, (CMD-Option-O-F) on powerup, and enter

**boot fw/node/sbp-2/disk:,\install\yaboot**

at the boot: prompt.  Be sure to actually type *boot* as the first verb.

---

