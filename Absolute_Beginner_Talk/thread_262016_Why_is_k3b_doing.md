---
title: "Why is k3b doing?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-09-21
I tried using again and still can't figure why it only bunrns my 16x +R verbatim at 4x any ideas. because the top window shows 16x but the bottom left says 4x All other programs I have tried burn at 16x.

Thanks

See pic to verify my problem.

---

### Post by orb9220 on 2006-09-21
bump

---

### Post by orb9220 on 2006-09-22
again

---

### Post by halitech on 2006-09-22
the top window is simply saying the speed the drive supports and the bottom portion is showing what the drive is actually doing for a write speed.

before you go to burn, try clicking on the auto detect speed button and then burn to see if that corrects it.

Also, is DMA turned on or off?

---

### Post by orb9220 on 2006-09-23
Dma is on by what the hdparm command says.

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

---

### Post by halitech on 2006-09-25
I'm not sure, mine only seems to burn between 2-6x and I know I've seen alot of posts saying people are having trouble with burning so might be inherit in Dapper.

---

### Post by orb9220 on 2006-09-25
Nope not dapper as my post says builtin cd burning in gnome as well as gnomebaker burn at 16x.

---

### Post by halitech on 2006-09-25
ok, misread that last part on the original post. I'm not sure unless it is because K3B is a KDE app and doesn't work as well in Gnome

---

### Post by nudnik on 2006-09-26
I get performance identical to Nero in Windows (16x) using K3b in Gnome with DVDs. Sounds like yet another hardware/media issue with Dapper. Fortunately it likes my machine up to a point.

GnomeBaker and my hardware despise each other, however.

---

