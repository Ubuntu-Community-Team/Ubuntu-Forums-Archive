---
title: "Dell 530N issues"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Trindol on 2007-12-21
I just got my 530N a couple days ago and overall it looks like it will work nicely but I have two complaints, things that really should not be an issue with an out of the box computer.

1. The 19in. widescreen resolution 1440x900 problem. I got it fixed, but they should have figured this out before shipping it.

2. The fan(s) come on and stay on full blast. I left the computer off overnight and when I booted it in the morning they did not turn on immediately. However when I restarted about 20 minutes later they came on again. It doesn't matter if I shut down, or restart, the fans are on full blast.

I have been looking at the forums for solutions, though it seems like the solutions out there are clumsy for a basic component. I have tried gkrellm and it tells me my temp is 40 and my fans are not on, though the clearly are. I also tried the i8kmon file at startup and it did not seem to work. I think these solutions are for laptops?

Anyway, I'm wondering if anyone has determined the real source of this fan problem, and not a fix that involves installing an application to cover it up.

I just saw that Dell released a bios update today. Currently I have 1.0.7 and the update is 1.0.10.

I am running 7.10

I don't mean to be too critical, overall I'm very satisfied, it's just this one little issue that should not be a problem with a new computer. Plus I can't sleep with the fans on...

Also: This is my first experience with Linux at all, so take it easy.

---

### Post by rfruth on 2007-12-21
I'm interested in the 530n (mini tower) can the BIOS control the fan(s) speed ?

---

### Post by Trindol on 2007-12-25
For the record, the fan issue seems to be solved.

It seems that every, or nearly every, recently shipped Dell 530 has this fan problem. The fan operates normally when the computer is first turned on. Upon resetting the fan kicks on full blast and does not stop until the computer has been off for awhile.

Turns out it is a BIOS problem.

Currently I am on BIOS 1.0.7. The fix is simply choosing "load defaults" in the bios menu. Change your CMOS setting back to whatever they should be and you're done. The CPU fan operates normally.

Dell released 1.0.10 recently. Rumor has it that this BIOS has fixed the issue. But I'm not gonna risk upgrading right now.

So, other than this frankly glaring quality control error, the 530 is doing well.

My latest issue is getting flash to work in Opera.

---

