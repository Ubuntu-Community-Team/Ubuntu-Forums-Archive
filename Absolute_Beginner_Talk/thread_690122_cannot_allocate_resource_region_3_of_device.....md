---
title: "cannot allocate resource region 3 of device...."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by jakelute on 2008-02-07
PCI: cannot allocate resource region 3 of device 0000:00:00.0
PCI: cannot allocate resource region 0 of device 0000:00:01.0

"lspci -vvv" shows that these two devices are:

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 64
        Region 0: Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Region 1: Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
        Region 3: Memory at <ignored> (64-bit, non-prefetchable)
        Capabilities: <access denied>


00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 99
        Region 0: Memory at 40000000 (32-bit, prefetchable) [size=64M]
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>


Can anyone recommend what I should do (if anything) -- I was wondering whether this problem is related to the other problem I've been having, which is a problem with temporary freezes -- everything stops for about ten minutes, and then it works again, but the clock is ten minutes slow -- unfortunately, this is happening numerous times every day. I'm on dual boot with XP at the moment.

Many thanks!

---

### Post by Pelham123 on 2008-02-09
Sounds like its related to the "Double clock speed" bug...

Easier if you do a google search on it (rather than me posting lots of links) as you know your system specs. Sounds like it can be bypassed with some boot parameters.

---

### Post by jakelute on 2008-02-09
Thank you very much for this. I'll look into it!

---

### Post by jakelute on 2008-02-09
hi again! I tried the procedures recommended here [http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281) -- but my CPU1 percentage is not particularly high -- so maybe in my case it's not the double clock speed bug?
Thanks!

---

### Post by jadonchristensen on 2008-02-25
I just upgraded my system using the Adept updater. All I remember is that I got some weird error when it was installing the upgrades, something about breaking packages. I rebooted, got the KDE flash screen, nVidia screen,  then just a black screen with a blinking cursor in the upper left corner.

I rebooted again and happened to catch the following error "cannot allocate resource region 3".

I rebooted again into Recovery Mode, then typed the following commands.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

[http://ubuntuforums.org/showthread.php?t=11103](http://ubuntuforums.org/showthread.php?t=11103)

That appeared to work. System is back to normal.

---

