---
title: "kernel modesetting problems"
date: 2009-10-28
forum: Apple Hardware Users
---

### Post by v41 on 2009-10-28
When using kernel-modesetting (KMS) with any recent kernel (2.6.30 or 2.6.31) on jaunty, the screen goes to 100% brightness and the brightness cannot be controlled with xbacklight or xrandr.  Turning off KMS restores brightness control.

There are several forum threads on  KMS and the solutions seem to be highly hardware specific.  In some cases the solution is to update the BIOS.  I haven't come across a thread specifically for apple hardware, so I thought I'd start one in the hope that someone has come up with a solution.

I noticed that the mactel-ppa contains xserver-xorg-video-intel-2:2.8.0, and the changelog mentions the backlight.  So I'm wondering whether that would solve the problem, even though it's older than the driver I'm currently using?

Details:

Harware:

[LIST]
[*] **model**: macbook-4.1
[*] **cpu**: intel-core-2-duo
[*] **graphics card:** intel-gm-965 (rev 03)
[/LIST]
 
Software: 

[LIST]
[*] karmic kernel (2.6.31-14)
[*]xserver-xorg-video-intel-2:2.9.0
[*]libdrm-intel1-2.4.14
[/LIST]

---

