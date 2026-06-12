---
title: "Installing / Configuring ISDN for Hylafax?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Nunnsby on 2008-02-08
Hi All, originally posted in Servers & Security, but no response has led me to reposting it here.

I am fairly proficient at using ubuntu, been using for about a year now, but I need help installing the ISDN stuff to use for Hylafax. Any help with steps would be greatly appreciated.

This is what I have so far: 

1) Default Gutsy SERVER Install
2) Winbond ISDN PCI Card

I am not too sure how to get the ISDN Card working. 

How do I install the drivers, test a dial-out, not network dial-out, just plain dial-out to see it brings up the ISDN interface at least?

DMESG tells me this:

[   36.306613] ISDN subsystem Rev: 1.1.2.3/1.1.2.3/1.1.2.2/1.1.2.3/1.1.2.2/1.1.2.2 loaded
[   36.433514] HiSax: Linux Driver for passive ISDN cards
[   36.433527] HiSax: Version 3.5 (module)
[   36.433534] HiSax: Layer1 Revision 2.46.2.5
[   36.433540] HiSax: Layer2 Revision 2.30.2.4
[   36.433545] HiSax: TeiMgr Revision 2.20.2.3
[   36.433551] HiSax: Layer3 Revision 2.22.2.3
[   36.433557] HiSax: LinkLayer Revision 2.59.2.4

and lspci tells me this:

00:0a.0 Network controller: Winbond Electronics Corp W6692 (rev 01)
        Subsystem: Technical Corp. Unknown device 5678
        Flags: medium devsel, IRQ 9
        Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d800 [size=256]

Any hints on where to start would be great, and maybe a bit of Hylafax help would be great too.

I have looked through Aptitude, but can't seem to find the mISDN stuff that everyone is talking about, and the ISDN4Linux appears to have been replaced by mISDN, so where to start? 

Do I even need the mISDN stuff for Hylafax? 

And what are the CAPI drivers/stuff?

All this talk about Capi4Hylafax? Can I use this instead? 

Thanks in advance.

Regards

Nunnsby

---

### Post by spiderbatdad on 2008-02-08
i think you might run the scanModem tool from synaptic then read the output file.

---

### Post by papuccino1 on 2008-02-08
I'm curious too.

---

