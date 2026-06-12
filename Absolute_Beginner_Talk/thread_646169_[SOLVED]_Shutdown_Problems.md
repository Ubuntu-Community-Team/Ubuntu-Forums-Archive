---
title: "[SOLVED] Shutdown Problems"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by absolution87 on 2007-12-20
Hi,
I have just recently been experiencing problems on my Compaq laptop running Ubuntu 7.10. Whenever i try to shut down the computer by clicking on the shutdown button, the system slows right down, the mouse still moves but all other functionality is lost.
Any help is greatly appreciated.
Thanks

---

### Post by Dr Small on 2007-12-20
What happens if you try it from the terminal ?
```
sudo shutdown -h
```

---

### Post by PmDematagoda on 2007-12-20
Could you post what you see in the terminal when you do:-

```
sudo shutdown -h now
```

---

### Post by absolution87 on 2007-12-20
when i type it in i get

shutdown: time expected
Try `shutdown --help' for more information.

---

### Post by PmDematagoda on 2007-12-20
> **Dr Small said:**
> What happens if you try it from the terminal ?
```
sudo shutdown -h
```

Dr.Small you need to have something after -h otherwise the command will not execute, either now(To shutdown the system immediately), +8(To shutdown the system after 8 minutes) or 0852(To shutdown the system at 8.52 AM).

Absolution87, you need to use the command I gave.

---

### Post by absolution87 on 2007-12-20
When i use the -now command the computer shuts down as it should, but the shutdown menu in to top right corner still hangs the computer. Is there any way to fix this?

---

### Post by Dr Small on 2007-12-21
> **PmDematagoda said:**
> Dr.Small you need to have something after -h otherwise the command will not execute, either now(To shutdown the system immediately), +8(To shutdown the system after 8 minutes) or 0852(To shutdown the system at 8.52 AM).

Absolution87, you need to use the command I gave.
Sorry about that. It's been a long time since I shut my system down :p

---

### Post by PmDematagoda on 2007-12-21
> **Dr Small said:**
> Sorry about that. It's been a long time since I shut my system down :p

:lolflag:, I just love to use the terminal to shutdown the PC sometimes, it seems to give me a feeling of power:D.

---

### Post by philinux on 2007-12-21
> **absolution87 said:**
> Hi,
I have just recently been experiencing problems on my Compaq laptop running Ubuntu 7.10. Whenever i try to shut down the computer by clicking on the shutdown button, the system slows right down, the mouse still moves but all other functionality is lost.
Any help is greatly appreciated.
Thanks

See link below for known bugs/workarounds.

Shutdown hanging is one of them.

---

