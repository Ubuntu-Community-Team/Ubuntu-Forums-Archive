---
title: "windows title bar dispear after recent upgrade"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by faif on 2007-12-07
hi all, I am using ubuntu 7.10 with thinkpad t60 ati x1300 chip. after recent upgrade (the one including firefox2.0.11) My windows title bar disappeared. I disabled compiz by select no effect, then open window for example firefox, it flipping  flashing a couple of times then title bar disappear again? It is quite annoy. anyone can give me a solution. PS 

Linux tbuntu 2.6.22-14-rt #1 SMP PREEMPT RT Mon Oct 15 01:05:51 GMT 2007 i686 GNU/Linux
I am using rt kernel. but it worked before upgrade.

Thanks

---

### Post by approaching on 2007-12-07
if your titlebars show up when you run a metacity --replace, then you may just have the windowing plugin in compiz unticked. not too sure about how that may happen, but i did do that on accident once. it may also be helpful to know if you are using something like emerald (at least to other people, not me).

---

### Post by DutyDuty on 2007-12-07
If you are using emerald and compiz, run ```
emerald --replace
then
compiz --replace &
```

---

