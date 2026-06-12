---
title: "System issue when logging in 18.04  Ubuntu"
date: 2019-09-08
forum: Apple Hardware Users
---

### Post by aldo82 on 2019-09-08
Hi, 
I've just installed Ubuntu 18.04 on my old MacBook early 2008, 2, 5 GB, running on dual-mode.

After logging in there is a recurrent pop message system eror detected, but I know this is only a symptom, not the cause,

so I decided to record the logs. Here are the cryptic lines. Many thanks in advance 
Aldo
Here are the cryptic lines:
[COLOR=#000000][FONT=Helvetica]
Logs begin at Thu 2019-09-05 18:40:33 CEST, end at Sat 2019-09-07 19:17:52 CE[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:04:50 aldo-MacBook kernel: Couldn't get size: 0x800000000000000e[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:04:50 aldo-MacBook kernel: MODSIGN: Couldn't get UEFI db list[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:04:50 aldo-MacBook kernel: Couldn't get size: 0x800000000000000e[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:04:50 aldo-MacBook kernel: Couldn't get size: 0x800000000000000e[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:05:01 aldo-MacBook kernel: Unable to load isight firmware[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:05:01 aldo-MacBook kernel: i915 0000:00:02.0: Invalid PCI ROM header s[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:05:01 aldo-MacBook kernel: PKCS#7 signature not signed with a trusted[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:05:02 aldo-MacBook kernel: Bluetooth: hci0: unexpected event for opcod[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:05:12 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_flip_done [[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:05:22 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_dependencie[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:05:32 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_dependencie[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:06:04 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_flip_done [[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:06:04 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_dependencie[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:06:04 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_dependencie[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:06:14 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_flip_done [[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:06:24 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_dependencie[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:06:35 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_dependencie[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:06:38 aldo-MacBook gnome-session-binary[1074]: CRITICAL: Unable to cre[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:06:51 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_flip_done [[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:07:01 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_dependencie[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:07:11 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_dependencie[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Sep 07 19:07:22 aldo-MacBook kernel: [drm:drm_atomic_helper_wait_for_flip_done [[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]lines 1-23[/FONT][/COLOR]

---

### Post by aldo82 on 2019-10-03
Issue is solved. I used  the REFind extended option several times, and the issue was gone.

---

