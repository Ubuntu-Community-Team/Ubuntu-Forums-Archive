---
title: "Wireless won't initiate after using NDISWRAPPER"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by schwahney on 2008-01-21
I've tried getting wireless working with two different wireless cards, TrendNet TEW-423PI and D-Link DWA-552. ndiswrapper shows hardware present in both cases after installing Windows card drivers. Running "lshw -C network" shows both cards present, though no line indicating driver or "on" state or anything (HELP says to verify this but does not say what one should see or how to change if not present). Network Settings show no wireless network to configure. HELP also says to use "System...Administration...Device Manager", but it is not present (not KDE desktop). This is very frustrating for us newbies. 

I've blacklisted  88w8335,  AR5416, mrv8335, and net5416 not knowing which of these is the actual name of the chipsets. Then rebooted.

Can someone please identify what I may do to get my wireless working or what info I can provide to diagnose the problem?:confused:

Thanks in advance.

---

### Post by Hightide on 2008-01-21
> **schwahney said:**
> 

Can someone please identify what I may do to get my wireless working or what info I can provide to diagnose the problem?:confused:

Thanks in advance

Hi
you should move your request to the 'networking and wireless' section on the homepage where the experts reside.

in the meantime,have you tried Kevdogs tutorial

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

:)

---

### Post by schwahney on 2008-01-21
Thanks - I'll do that. 
I just tried your suggested link and got stuck in the middle. I got:

ndiswrapper -v
utils version: 1.9
driver modinfo: could not find module ndiswrapper

Bummer. Thanks - I'll repost in expert section.

---

