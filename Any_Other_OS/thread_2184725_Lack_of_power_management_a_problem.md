---
title: "Lack of power management a problem?"
date: 2013-10-30
forum: Any Other OS
---

### Post by DisappearingOak on 2013-10-30
Hello, I'm using ElementaryOS Luna and I like the clean desktop with the dock, but I have a question.. is it OK to use the open drivers though they do not have dpm before kernel 3.11? I'm worried about my chip overheating, but I don't know how to measure temp as it's an onboard Radeon hd 4250. Is that a problem or can I just keep using elementaryos?

---

### Post by Stinger on 2013-10-30
I have no problem with my Radeon hd4670, I have excelent 2D and 3D performance, no extreme noises from the gpu-fan, very quiet.

Else you got three choises:

[LIST=1]
[*]Stay on the stable branch and try using the [AMD Catalyst Legacy driver from Tomasz Makarewicz ppa]("https://launchpad.net/~makson96/+archive/fglrx?field.series_filter=precise")
[*]Use the [LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") from saucy or trusty ( kernel and Xserver )
[*]Use the  ( unstable ) [elementary Daily ppa]("https://launchpad.net/~elementary-os/+archive/daily") on a saucy or trusty base installation
[/LIST]

Hope it helps :)

---

