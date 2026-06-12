---
title: "So close to hardware 3D - do I need to recompile MESA/libdrm?"
date: 2014-10-01
forum: Apple Hardware Users
---

### Post by themacmeister on 2014-10-01
Firstly, I am using Mint 11 PPC on my G5 PowerMac DP 2.5GHz powermac7,3, but the MintPPC forums are kaput for new users... still waiting for approval days later.

I have attached my xorg.conf and Xorg.0.log

It seems there is an issue with my Mac Radeon 9600 BIOS not being x86 and failing to read.

Apart from that, I am lost. Any help greatly appreciated. Thanks.

[ATTACH]256841[/ATTACH]

---

### Post by themacmeister on 2014-10-01
I downgraded 4 mesa/glx/glu packages to Mesa 7.11ubuntu33 and BOOM:

OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV350 4152) PowerPC 64/Altivec TCL
OpenGL version string: 1.5 Mesa 7.11

My transparency works, and framerates went up x10. There seems to be no difference in visuals/performance with AIGLX at all, but I am now suffering from terrible flickering in some titles. If anyone knows a solid xorg.conf with the radeon or ati driver with edits to fix graphics, please let me know what to put in there.

I am using a Radeon 9600 xt with 128MB vRAM. Running XFCE4 @ 1280x1024x32 at the moment. (possibly x24).

Many thanks in advance.

---

### Post by tgalati4 on 2014-10-01
I'm impressed with the progress that you have made on this old hardware.

Have you inserted the correct gtf settings into xorg.conf?

> tgalati4@Mint14-Extensa ~ $ gtf 1280 1024 60

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vs


Your numbers will be different.

---

