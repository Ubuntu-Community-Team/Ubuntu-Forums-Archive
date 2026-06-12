---
title: "JACK suitability for multiple Web I/O's on one computer"
date: 2012-03-05
forum: Any Other OS
---

### Post by bcschmerker on 2012-03-05
I am currently considering retrofitting JACK'S Audio Connection Kit to a Microsoft® Windows® 7.0.8001 installation (MultiProcessor Kernel 6.1.7601); Win 7 inherited its audio-signal stack from Windows® 6.0.6002.  As of 5 March 2012, my Asus® CM1630-06 (Advance Micro Devices® Athlon II® X2 220, 760G chipset), augmented with the same vendor's EAH6850DC/2DIS/1GD5 PCIe x16 video adapter (Advance Micro Devices® R970 Pro GPU, Asus® DirectCu® fan/heatsink) and XONAR® Essence™ STX PCIe x1 audio adapter (Asus® AV-100 DSP, mfd. for ASUSTeK Computer by C-Media International Inc.), plus Antec® TP-750 Blue PSU, performs well enough in basic audio tasks but could use a completely new DLL/DRV set to allow routing audio signals to and from different Applications (e.g., the I/O of Mozilla® Firefox 10.0.2 with Adobe® Flash™ 11 plug-in to the XONAR®; Microsoft® Internet Explorer™ 9.0 with the Silverlight™ 3 ActiveX to the currently shut-down, as of 5 March 2012, planar VIA® VT1021).

That JACK can route audio across different hardware sources and sinks on one computer, is known.  I have a need for routing different incoming and/or outgoing PCM signals from Ethernet/Internet via different applications to specific audio sources and sinks.  Has this been done reliably; and if so, what need I watch out for, in terms of configuring JACK for this multiple-Web-stream issue?  Any help would be appreciated.

---

