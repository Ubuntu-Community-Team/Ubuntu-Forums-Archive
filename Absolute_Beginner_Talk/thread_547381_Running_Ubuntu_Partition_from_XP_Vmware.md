---
title: "Running Ubuntu Partition from XP Vmware"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Torn on 2007-09-09
Im trying to run my ubuntu installed partition from my xp.
rebooting into each os claiming to be a hastle.

---

### Post by funrider on 2007-09-10
succeeded?
need help?

---

### Post by djchandler on 2007-09-10
> **funrider said:**
> succeeded?
need help?

I ran Xubuntu under QEMU in XP. I needed lots more power to be satisfying (Athlon 64 2800 a couple of years ago.) A separate pIII with half a gig was way more satisfying.  You'd be better off finding an old P4, putting Ubuntu on a separate box, and have both computers running side-by-side. Get a KVM switch, and you have the best of both worlds. If there's a decent computer recycling center nearby, or you can pick one up on ebay or something, you're set.

I've not run VMWare, but emulators are pretty much doing the same thing. The system differences still have to be translated before execution, and graphics can't keep up. Come to think of it, I'd rather run VNC over 100mb/sec ethernet than an emulator if you don't want to worry about a KVM switch. Gigabit would be better, of course. That's my next network project. There's four computers for the two of us, plus a TCP/IP printer, an old Laserjet 4+.

DJ

---

### Post by djchandler on 2007-09-10
> **Torn said:**
> Im trying to run my ubuntu installed partition from my xp.
rebooting into each os claiming to be a hastle.

Torn,

Your drivers probably won't work if installed as a dual-boot setup. The emulator, VMware, QEMU, or any other emulator, imposes a compatibility layer (just as WINE does in Linux) and uses common drivers to enhance software compatibility.

You must re-install Ubuntu while running VMware or QEMU to successfully boot that partition, unless you know what hardware is modeled in the emulator layer, and how to edit all your configuration files.  The free Microsoft Virtual PC only allows emulation of Microsoft operating systems or IBM OS2.

DJ

PS OP, have you solved this or what?

---

