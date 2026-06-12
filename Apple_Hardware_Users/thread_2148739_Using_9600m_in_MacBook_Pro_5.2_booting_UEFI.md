---
title: "Using 9600m in MacBook Pro 5.2 booting UEFI"
date: 2013-05-26
forum: Apple Hardware Users
---

### Post by ronyclau on 2013-05-26
Hi everyone,

I am running Ubuntu 12.10 Desktop (64-bit) on my MacBook Pro 5.2. The machine has 2 graphic cards, namely NVidia 9600m GT and 9400.
Ubuntu boots in UEFI mode and lspci reports that both cards are activated.
I am using Nvidia's proprietary driver. nvidia-setting shows that the 9400 is hooked to the X screen.

I tried to set the 9600m as the display in xorg.conf but X just started in failsafe mode.

I don't need GPU hot-switching. What I need is only using 9600m in Ubuntu (set on boot is ok), as my MBP is always AC connected so power is not a concern.
I have searched with Google but I could only find ways to disable the 9600m.

I would like to ask whether there is any way to select the 9600m as the X display? Or I need to resort to BIOS booting?

Many thanks,
Ron

---

