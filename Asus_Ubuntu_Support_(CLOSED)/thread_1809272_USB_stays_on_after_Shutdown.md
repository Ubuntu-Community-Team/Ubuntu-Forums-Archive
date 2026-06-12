---
title: "USB stays on after Shutdown"
date: 2011-07-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Unterseeboot_234 on 2011-07-21
I have two ASUS motherboards

M2NPV-VM AM2
and
M4A87TD AM3

Both run the AMD64 cpu / 64-bit Ubuntu, the M4A87 is the more modern by 4 years.

At Shutdown, the USB devices all power down with the first board, the lights turn off. Plug the same peripherals to the 2nd board, power up and then Shutdown, the USB devices lights don't turn off. The laser mouse still has his blue light shining. The external HD still has a power light. I have to remember to switch-off my power strip that supplies the computer and monitor.

Is there a setting in BIOS, or a mobo DIP switch that changes the USB behaviour with the power participation?

---

### Post by Unterseeboot_234 on 2011-07-24
Asus forum gave me a solution (if anyone follows this thread)

In BIOS, for Power menu
Eup submenu
Eup Ready [ Disabled ] <=> change that <=> [ Enable ]

Boot into Win or Ubuntu, shutdown gives me USB devices without power lights.

And, I might have overlooked the lit-up USB externals if it wasn't for the fact that I own two Asus boards.

---

