---
title: "Weird self-fixing problem booting G5 after kernel update"
date: 2012-06-15
forum: Apple Hardware Users
---

### Post by nadrojksc on 2012-06-15
I recently replaced Mac OS X with Ubuntu 12.04 on my dual G5 tower. Everything works pretty great so far; however, I'm having a very odd problem that seems to manifest after kernel updates. 

When I reboot the machine after a kernel update, I see the bootloader (yaboot?), but it just hangs on that screen. It's not responsive to any sort of input. After that, if I reboot the machine again, I hear the startup chime, but I don't get anything on the screen at all. The box just sits there, seemingly bricked (I checked, it's not coming up on the network so I'm pretty sure it's not booting at all.) Subsequent reboots will produce the same thing, or rarely sometimes if I'm lucky I'll get the (still unresponsive) bootloader screen.

The only keyboard I've got around (Model M + USB converter) lacks a Windows (aka Command) key, so I'm unable to try all the different startup key combinations. However, just holding Alt (aka Option) doesn't seem to help; it doesn't bring up the firmware list of bootable media - I just get the black screen. I'll try to borrow a USB keyboard with more keys from someone soon.

Here's the REALLY weird part: after messing with it for an hour or so, I'll give up in frustration and wander off or go to bed. The next day, when I try to power on the machine, suddenly everything is happy again! It boots right up to the login screen and runs with no issues.

Anybody have a clue?

---

### Post by fbicknel on 2012-06-15
Once had an Asus AMD motherboard that would occasionally hang after it was in use for a while.  Sometimes it would reboot on reset, but more often than not it would hang on boot.  Leave it off for a bit and it would cool off and you could boot it and use it for another half hour or so before it would hang again.

Finally tracked it down to a southbridge overheating.  

I can't tell for sure that's your problem, but you might take a can of freeze spray to individual components and see if you can get past the boot hang by cooling one component at a time.

If you're real patient.  <grin>

---

### Post by nadrojksc on 2012-06-17
I thought it might be heat-related, but again, it only seems to happen after a kernel update... Otherwise, I'm able to reboot the box without any trouble. It doesn't seem to have any heat problems otherwise; once it's up, I've run it for days without issue, compiling all sorts of stuff.

---

### Post by rsavage on 2012-06-18
Are you for some reason running ybin (which changes nvram) after every kernel upgrade?

---

