---
title: "G4 powermac gigabit cannot open cd?"
date: 2009-09-29
forum: Apple Hardware Users
---

### Post by s0liddi on 2009-09-29
Currently testing a motherboard, cpu + gpu from G4 powermac, i'm facing problems with tying to get installer going. 

Pressing C does nothing, so time to google. Suggestions gone thru: Reset VMRAM, PRAM, etc

So i opened Open Firmware and tried to get installion going manually:

dev cd:,  ok
boot cd:,\install\yaboot   can't OPEN boot cd:,\install\yaboot

So that can be translated No go. Any ideas :confused:
Thos i'm little supsious about how well my dvd drive or that DVD-RW disk works along with G4.

---

### Post by s0liddi on 2009-09-30
solved!
> I finally tracked down the cause of the problem. For me, somehow the aliases hd and cd got mixed up (and no amount of PRAM resetting fixed it..) and so "boot cd:,\install\yaboot" actually pointed to the master hard drive instead of to the cd drive, so I typed in "boot hd:,\install\yaboot" and it booted off the cd.

That was the problem :D!

---

