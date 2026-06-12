---
title: "Any distro that works out of the box with Macbooks?"
date: 2008-07-17
forum: Apple Hardware Users
---

### Post by liquidfunk on 2008-07-17
I have a MacBook 2,1 and I fancy running some form of Linux on it.

 Any you know of that run out of the box, or any that are being developed to run out of the box.

 (Excluding Elive Macbook as it's outdated).

 Ideas?

---

### Post by cyberdork33 on 2008-07-17
What do you mean exactly...? several distros work on Macbooks.

---

### Post by Playercoca on 2008-07-17
wasn't there something called yellow dog or something?

---

### Post by liquidfunk on 2008-07-17
I mean one that works without having to tweak anything. 

 So wireless works straight away, the iSight works, bluetooth etc. Without any fiddling. As though it was shipped with the Macbook.

 And no Yellow Dog is for PowerPC's, so iBook G3/4/5, PS3, etc.

 Mine is an Intel machine.

---

### Post by flaggh on 2008-07-17
Isn't the hardware incompatibility pretty much universal to all linux distros since it has more to do with kernel and driver support than the software that is included with the distro?

---

### Post by cyberdork33 on 2008-07-18
> **liquidfunk said:**
> I mean one that works without having to tweak anything. 

 So wireless works straight away, the iSight works, bluetooth etc. Without any fiddling. As though it was shipped with the Macbook.

Well, Apple uses proprietary hardware for wifi that doesn't have a decent driver, so you have to use ndiswrapper and a windows driver, and there isn't anyone that can legally distribute these drivers without a license from Broadcom, so no there. (Some machines have atheros wifi which is better, but it will take a little while for madwifi to support the newer chipsets, then they should "just work").

The iSight requires firmware loading, and the firmware is part of OS X, so again, you cannot legally distribute that. Further, you probably can't technically even possess it unless you have a licese for OS X. So, unless you want a fight with Apple's legal team, I wouldn't suggest including it in your distro either. Thankfully, the very newest iSights in the MacBook Air and MacBook Pro doesn't require the firmware loading, so that may not be an issue for too much longer.

Bluetooth does "just work" as far as I know. There isn't a Mactel out there that need configuration for the bluetooth hardware to be operate. If you are talking about connecting devices, then that is a differnet issue. It is not a "hardware support" but more like a "user friendliness" issue. I don't know if it is a Ubuntu/Debian specific issue, but there might be other distros out there that make connecting bluetooth devices easier. The GUI app to use your bluetooth hardware has made drastic improvements in Ubuntu in the last few releases. It will take a while for all the problems to get flushed out.

---

