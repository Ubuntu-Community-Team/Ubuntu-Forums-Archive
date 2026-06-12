---
title: "Random crashes"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Wien_Sean on 2006-09-25
Ok this seems to be a driver problem, as far as I can figure. I have an M6809 (Laptop)  with an AMD64 and 1.25 gb of ram. After using the computer for a bit, say three hours, the fan goes on high for a few seconds and then the computer shuts off. After rebooting this will happen in quicker and quicker if rebooted shortly after the first crash. I used to have this problem with XP but SP2 and a series of specific driver updates (which I can no longer remember) solved the problem. I am working off the Breezy install of 64 distro (I had to do a netboot install). I doubt this has been addressed in the newer version so I haven't upgraded.I have been working on this thing for the last week and some days and now that I have in running I cannot stand the thought of trying to figure this one out. Anyone have any ideas? Thanks!

---

### Post by Kateikyoushi on 2006-09-25
From the spinning fan and the quicker and quicker shutdown I would say the problem might be that your system gets too hot and the overheat protection turns it off.
Can you check the temperature of the processor ? Power saving profile might help too.

---

### Post by Wien_Sean on 2006-09-25
See now that's what I thought for about a year. I was using XP and I looked for that year for a fix. I had a cooling pad under the thing for example. The problem is the bios is rather limited and has no core temp, or any temp for that matter. In a anycase I found it to be a driver issue. I can run very taxing programs in a properly set up XP install or in dos, such as those stress tests found on the Ultimate boot cd, and not a problem. I had XP installed and no crashes for the past year and I was running the thing for months at a time without a crash. Now I came home after the install had finished just hours before and sat down to use it and it crashed like it used to. The fix before was a CPU driver as I recall.

---

### Post by Kateikyoushi on 2006-09-25
If a driver fixed it before then my best bet is to search on the AMD [website]("http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_9706,00.html").
The cpu driver and the cool and quiet will reduce the temperature of the system.

---

### Post by stilus on 2006-09-25
I have similar problems with an older fujitsu-siemens laptop. setting acpi=off in grub has fixed this for now, but that is quite a dirty hack. This sounds like it might be related to:
[https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/22336](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/22336)

No real fix that I know... anyone?

kind regards,

stilus

---

### Post by Wien_Sean on 2006-09-25
I guess I will try that. In all honesty though this is not a hardware issue. I am back to my XP install and will find a setup for Motherboard Monitor and do a stress test just to see if the temp get to the point where it should reboot.

---

### Post by Wien_Sean on 2006-09-25
So it seems that I cannot read the thermal diod on the mobo so that is out. But I did find a thread somewhere else and it seems that the problem is the diod is reporting the wrong temp and causing the shut down. It seems the drivers that I am using in XP solve the problem by reading the diod reports differently. I don't have these problems in XP or OSX anymore and there has to be a fix for Linux, it's just going to take me a while.

---

### Post by Wien_Sean on 2006-09-25
> **stilus said:**
> I have similar problems with an older fujitsu-siemens laptop. setting acpi=off in grub has fixed this for now, but that is quite a dirty hack. This sounds like it might be related to:
[https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/22336](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/22336)

No real fix that I know... anyone?

kind regards,

stilus


Will take a look at this later, I am to knackered to deal with it now.

---

