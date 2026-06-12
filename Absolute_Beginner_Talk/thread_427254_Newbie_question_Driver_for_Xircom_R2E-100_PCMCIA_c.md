---
title: "Newbie question: Driver for Xircom R2E-100 PCMCIA card"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Rover1288 on 2007-04-29
Hi everyone,

I have just managed to install UBuntu 7.04 onto my old Toshiba Satellite laptop which has a Xircom RealPort2 (R2E-100) pcmcia ethernet card.

It does not seem to work:( . Does anyone know where I can find a driver for this and how to get this working?

Thanks.

---

### Post by NeoTaoistTechnoPagan on 2007-05-01
Just guessing - try adding "dopcmcia" in your kernel boot params in the /etc/grub/menu.lst file.

After you edit it, make sure you run "update-grub" afterwards.

If it's a really old system, I would also add "noapic" as well.

---

