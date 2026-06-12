---
title: "I installed a capture card, but how do I know if it's working?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-12
```

00:0d.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: Technotrend Systemtechnik GmbH DVB T-1500
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (3750ns min, 9500ns max)
        Interrupt: pin A routed to IRQ 15
        Region 0: Memory at fdffb000 (32-bit, non-prefetchable) [size=512]

```
```

nibbles@nibbles-desktop:~$ grep -i dvb /var/log/messages
Feb 12 20:24:58 nibbles-desktop kernel: [   26.827916] saa7146: register extension 'budget_ci dvb'.
Feb 12 20:24:58 nibbles-desktop kernel: [   26.828015] DVB: registering new adapter (TT-Budget-T-CI PCI).
Feb 12 20:24:58 nibbles-desktop kernel: [   26.861691] input: Budget-CI dvb ir receiver saa7146 (0) as /class/input/input4
Feb 12 20:24:58 nibbles-desktop kernel: [   27.005399] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Feb 12 21:44:36 nibbles-desktop kernel: [   27.597060] saa7146: register extension 'budget_ci dvb'.
Feb 12 21:44:36 nibbles-desktop kernel: [   27.597164] DVB: registering new adapter (TT-Budget-T-CI PCI).
Feb 12 21:44:36 nibbles-desktop kernel: [   27.635002] input: Budget-CI dvb ir receiver saa7146 (0) as /class/input/input4
Feb 12 21:44:36 nibbles-desktop kernel: [   27.657758] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Feb 12 21:48:55 nibbles-desktop kernel: [   27.354199] saa7146: register extension 'budget_ci dvb'.
Feb 12 21:48:55 nibbles-desktop kernel: [   27.354596] DVB: registering new adapter (TT-Budget-T-CI PCI).
Feb 12 21:48:55 nibbles-desktop kernel: [   27.393924] input: Budget-CI dvb ir receiver saa7146 (0) as /class/input/input4
Feb 12 21:48:55 nibbles-desktop kernel: [   27.472990] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Feb 12 22:17:50 nibbles-desktop kernel: [   26.238712] saa7146: register extension 'budget_ci dvb'.
Feb 12 22:17:50 nibbles-desktop kernel: [   26.238823] DVB: registering new adapter (TT-Budget-T-CI PCI).
Feb 12 22:17:50 nibbles-desktop kernel: [   26.276060] input: Budget-CI dvb ir receiver saa7146 (0) as /class/input/input1
Feb 12 22:17:50 nibbles-desktop kernel: [   26.821209] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
nibbles@nibbles-desktop:~$ 




```

Not sure what else to do...

---

### Post by Dr Small on 2008-02-12
For the sake of the rest of the readers, what is a "capture card"?

---

### Post by klemens on 2008-02-12
could you be a bit more specific on the card?

---

### Post by jan quark on 2008-02-12
had to look it up too

[http://en.wikipedia.org/wiki/Capture_card](http://en.wikipedia.org/wiki/Capture_card)

---

### Post by joesmith1234 on 2008-02-12
> **klemens said:**
> could you be a bit more specific on the card?

Technotrend Systemtechnik GmbH DVB T-1500

---

