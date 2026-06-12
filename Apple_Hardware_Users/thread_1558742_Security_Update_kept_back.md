---
title: "Security Update kept back?"
date: 2010-08-22
forum: Apple Hardware Users
---

### Post by ayenack on 2010-08-22
Hello all.

I've installed Ubuntu 10.04 PPC on a 12" PowerBook G4. I've managed to get everything working fine and have the system updated other than:-

[B]linux-image-2.6.32-24-powerpc (New Install)
linux-image-powerpc
linux-powerpc
[/B]

Which have been kept back.

Has anyone installed these updates and if so did they break your system?

I don't want to install them and find they break the install.

Thanks in advance for any advice on this.

---

### Post by ayenack on 2010-08-24
Bump.

Anyone got any ideas on this?

Thanks.

---

### Post by avtolle on 2010-08-24
I'm running 10.04, have installed said kernel which was upgraded this a.m. from 2.6.32-24.41 to 2.6.32-24.42. No problems here. I don't recall the "hold back"; perhaps it was due to a problem resoled by the latest upgrade? (G4 Cube, BTW)

---

### Post by ayenack on 2010-08-25
Thanks for that avtolle. I'll update and see what happens.

Edit:- avotlle can you tell me what graphics card you're running? Thanks.

Strangely it's only kept back from command line and not in update manager.

Was trying to think if there's anything I've installed that might cause it to be held back, all I can think of is the nouveau drivers for nvidia graphics card.

I've installed on a PowerBook G4 12" and had some fun and games when installing. When I installed and rebooted the, system would run fine other than wireless (which is an easy fix if you got a wired connection) but as soon as I powered of, the system would boot to a black screen. Scratched my head for a day or two and re-installed a few more times to confirm the error then found that the answer was to install the nouveau drivers on a new install before powering off, then all of a sudden everything worked.

So hope the new kernel will be able to handle this. MAy as well find out now before I get to much on the lappy to take the risk.

I'll post back with results.

ayenack.

---

### Post by avtolle on 2010-08-26
The video card in the Cubes is an ATI Rage 128. Sorry for the delay in responding.

---

### Post by ayenack on 2010-08-27
Not a problem. I'm not so sure I'll update now as I've a feeling it'll break the system and I've now got quite a bit of stuff on it.

I'll have to make my mind up soon though.

Thanks for the help. I'll post back if I do update on how it went.

---

### Post by ayenack on 2010-08-31
OK Finally took the plunge and updated the kernel. After update I first did a system restart and all was working so then decided to power off and on again to see if all would be OK and it works fine.

Did not need to re-install nouveau drivers or re-configure xorg.conf before shutdown. Just did the original update and everything works fine.

....PHEWWwww

---

