---
title: "frequent short freezes in firefox"
date: 2011-10-10
forum: Any Other OS
---

### Post by Sonic Reducer on 2011-10-10
quite often firefox will freeze for a short time while i am using it, particularly when i click a bookmark in the toolbar. FF will lock up, the entire window will turn grey and it will stay that way for a couple minutes. it will be fine after it "defrosts," at least until the next time it freezes

i followed [this guide]("http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/") hoping it would help but has not changed anything.

i'm running Linux Mint but i dont know what version (only a few months old) and i think i should point out that the computer is usable save for FF when it's frozen. i can access other windows, watch movies, type documents, etc while FF is frozen. it is only the the FF window that freezes

---

### Post by Sonic Reducer on 2011-10-11
i happened to have the system monitor open when FF froze again, both cores on my dual core laptop were fluctuating normally, and right when FF froze CPU2 spiked to 100% and did not waver until FF unfroze.

so what i know right now is that firefox is the only app that freezes on me, and when it freezes the cpu usage in one of my cores spikes to 100% until firefox unfreezes

---

### Post by Perfect Storm on 2011-10-11
Moved to Other OS/Distro Talk.

---

### Post by el_koraco on 2011-10-12
It seems there's an issue with Firefox 7 and Nvidia cards. If you have an nvidia card, you ca either downgrade your Xserver version, or use another browser until this gets cleared out.

---

### Post by MichaelGld on 2011-10-12
> **Sonic Reducer said:**
> quite often firefox will freeze for a short time while i am using it, particularly when i click a bookmark in the toolbar. FF will lock up, the entire window will turn grey and it will stay that way for a couple minutes. it will be fine after it "defrosts," at least until the next time it freezes

i followed [this guide]("http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/") hoping it would help but has not changed anything.

i'm running Linux Mint but i dont know what version (only a few months old) and i think i should point out that the computer is usable save for FF when it's frozen. i can access other windows, watch movies, type documents, etc while FF is frozen. it is only the the FF window that freezes


I am having the exact same problem. I am running 10.04 and have a GeForce 7300 GS video card. It even happens if I run Firefox in safe mode.

---

### Post by Sonic Reducer on 2011-10-13
i'm running an Acer AS5672WLMi with a ATI Radeon Mobility X1600 graphics card. i dont know what driver i'm using (never changed it so it the LMint default)

here's my modprobe if it helps
```
ryan@linux-laptop ~ $ lsmod | grep radeon
radeon                900494  3 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   184164  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  1 radeon
```

---

### Post by Algus on 2011-10-15
> **el_koraco said:**
> It seems there's an issue with Firefox 7 and Nvidia cards. If you have an nvidia card, you ca either downgrade your Xserver version, or use another browser until this gets cleared out.

Wow, thanks for the tip! I've got the same problem on my Windows PC (I actually switched to Chrome) but didn't know it was because of my graphics card! I've got an Nvidia GeForce 8500 :/

---

### Post by el_koraco on 2011-10-15
> **Algus said:**
> Wow, thanks for the tip! I've got the same problem on my Windows PC (I actually switched to Chrome) but didn't know it was because of my graphics card! I've got an Nvidia GeForce 8500 :/

Yah, apparently it's cross platform (I guess dwm is acting up on Win). Dunno how that can be remedied, you don't *downgrade* Explorer, maybe pull in an older version of the driver?

---

