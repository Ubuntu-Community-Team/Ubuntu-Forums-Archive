---
title: "Need lead on interpretation of freeze"
date: 2011-04-05
forum: Any Other OS
---

### Post by nnjond on 2011-04-05
Hi,

I have a problem with scrn and keyboard freezes.
This time it only threatened to crash, and  I've noticed something in /var/log/ mssge that might lead to a solution (if I understood it) Any advice?  Please.


Apr  5 06:42:04 Den-mint kernel: [  233.209761] EXT4-fs (sdc1): warning: mounting fs with errors, running e2fsck is recommended


It's imediate context is below.

```


Apr  5 06:40:32 Den-mint kernel: [  119.061354] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
Apr  5 06:40:12 Den-mint kernel: [  120.608847] EXT4-fs (sdb8): re-mounted. Opts: errors=remount-ro,commit=0
Apr  5 06:40:14 Den-mint kernel: [  123.063407] EXT4-fs (sdb8): re-mounted. Opts: errors=remount-ro,commit=0
Apr  5 06:40:16 Den-mint nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Apr  5 06:40:17 Den-mint nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Apr  5 06:40:25 Den-mint nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Apr  5 06:40:25 Den-mint nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Apr  5 06:41:12 Den-mint kernel: [  181.004022] Clocksource tsc unstable (delta = -109589020 ns)
Apr  5 06:42:04 Den-mint kernel: [  233.209761] EXT4-fs (sdc1): warning: mounting fs with errors, running e2fsck is recommended
Apr  5 06:42:05 Den-mint kernel: [  233.459227] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
Apr  5 06:53:01 Den-mint pulseaudio[1738]: ratelimit.c: 1120 events suppressed
```

---

### Post by NightwishFan on 2011-04-05
Do you get to a desktop or tty? If so run this command:
```
touch /forcefsck
```

It will check your drives on reboot.

(Or you could boot into a live cd and check them with gparted)

---

