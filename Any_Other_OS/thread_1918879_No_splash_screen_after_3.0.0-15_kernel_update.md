---
title: "No splash screen after 3.0.0-15 kernel update"
date: 2012-02-01
forum: Any Other OS
---

### Post by bach on 2012-02-01
> Today I updated to the 3.0.0-15 kernel, and afterward the Ubuntu splash screen no longer appears during startup and shutdown. After the GRUB menu I get a black screen with a flashing cursor for several seconds, followed by a purplish screen with plain "Ubuntu 11.10" text, four dots underneath, and then some low-level boot messages. The same thing happens when shutting down.

I checked the GRUB configuration, and the "ro quiet splash" options are still there. The only difference I see between the updated configuration and an old backup is that "vt.handoff=7" has been added at the end. The backup is from August, however, and the vt.handoff option might have been there for a while.

I don't see any other problems, and it seems to be only cosmetic, but I'm curious what's going on. Any ideas?

I have the same problem: blank screen at boot after upgrading to kernel 3.0.0-15. I run Linux Mint 12 on a DELL Latitude E6510 with Intel GPU.

---

### Post by Quatrix on 2012-02-01
> **bach said:**
> I have the same problem: blank screen at boot after upgrading to kernel 3.0.0-15. I run Linux Mint 12 on a DELL Latitude E6510 with Intel GPU.

Is this relevant?

[http://forums.linuxmint.com/viewtopic.php?f=47&t=91936](http://forums.linuxmint.com/viewtopic.php?f=47&t=91936)

---

### Post by Perfect Storm on 2012-02-01
Moved to Other OS/Distro Talk.

---

