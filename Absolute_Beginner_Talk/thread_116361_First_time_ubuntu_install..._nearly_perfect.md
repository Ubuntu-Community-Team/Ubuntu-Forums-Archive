---
title: "First time ubuntu install... nearly perfect"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by meglamaniac on 2006-01-12
In fact this niggle is so small, in the grand scheme of things, that it barely counts. Anyway.

I have an old Toshiba Satellite Pro 4270 which is quite happy to run Ubuntu. I mainly use it in the library. Unfortunately, every time it boots up I get two rather loud beeps from the PC speaker just about the time X is starting up. This is not very desirable in a quiet environment.

Is this intentional and part of the init/rc setup, or is something complaining?
If it's intended, some guidance on how to stop it would be appreciated.

Thanks.

---

### Post by az on 2006-01-12
[QUOTE=meglamaniac]In fact this niggle is so small, in the grand scheme of things, that it barely counts. Anyway.

I have an old Toshiba Satellite Pro 4270 which is quite happy to run Ubuntu. I mainly use it in the library. Unfortunately, every time it boots up I get two rather loud beeps from the PC speaker just about the time X is starting up. This is not very desirable in a quiet environment.

Is this intentional and part of the init/rc setup, or is something complaining?
If it's intended, some guidance on how to stop it would be appreciated.

Thanks.[/QUOTE]
Is the pcspkr modules loaded?  Maybe you can blacklist it.
/etc/hotplug/blacklist

---

### Post by Sef on 2006-01-12
Try this:   System ----> Preferences -----> Sound ----> General ------> unclick Enable Sound Server Startup.

---

