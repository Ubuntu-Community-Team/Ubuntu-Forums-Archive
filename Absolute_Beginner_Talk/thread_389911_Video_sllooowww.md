---
title: "Video sllooowww"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by JasonWard on 2007-03-21
I have installed Ubuntu 6.10 and the screen is slow, very slow.

A friend has told me to use

lspci -vv to see what the video hardware is and it says for the video

01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 11) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Region 1: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at fbef0000 [disabled] [size=64K]
        Capabilities: <access denied>

Can anyone help me?

Thanks
Jason

---

### Post by JasonWard on 2007-03-21
I've subsequently found this

[http://wiki.openchrome.org/pipermail/openchrome-users/2006-December/002527.html](http://wiki.openchrome.org/pipermail/openchrome-users/2006-December/002527.html)

Which may be my problem... but I don't know... and I have no idea what do with some source code!

Jason

---

### Post by taurus on 2007-03-21
Look at Section 4 of this guide on how to build something from source.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by JasonWard on 2007-03-21
Do you think it will solve my problem?

---

### Post by catnap on 2007-03-23
I had what I think was a very similar problem, and have just successfully used the reccomendtaions at:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

However I reckon it would be a good idea to try and identify the video/southbridge chip more accurately.  lspci gave me a similar output on my machine, yet did not identify the   video driver chip - I obtained this by looking at the mobo spec and the manual.

Hope this helps

---

### Post by JasonWard on 2007-03-23
A friend compiled the code for me and I gave the new driver a go, and everything is great now.

Anyone else want the X86 VESA driver that isn't slow I got it here [http://vesavideodriver.jasonward.co.uk/](http://vesavideodriver.jasonward.co.uk/)

Jason

---

