---
title: "2009 Mac mini - grey screen for AGES before Ubuntu boots"
date: 2009-12-04
forum: Apple Hardware Users
---

### Post by youbuntu on 2009-12-04
Hey all.

I have a 2009 Mac mini with Karmic x86 on it, but one thing I cannot work out, is why the grey Apple screen (is it EFI?) sits there for about 30 seconds BEFORE the black screen which boots Ubuntu?.

Is this EFI, because if so, I am *sure* the partitioner should have wiped my entire drive, *including* EFI partition, when I did the install (this Mac is Ubuntu only btw).

Can someone tell me how to wipe/eradicate this time-consuming grey Apple screen?.

Thankyou :)

---

### Post by tom4everitt on 2009-12-05
I think it will always be EFI booting your mac, just like it will always be BIOS booting your pc (no matter if you have windows, linux or both on it). EFI is essentially the BIOS for macs (although it is much better and newer of course :) )

[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

I'm afraid I don't know many details about how it works, or what you can do to speed it up. Perhaps dear Google has an idea?

---

### Post by bean123 on 2009-12-05
It's slow when you try to boot into BIOS mode directly. However, you can load grub EFI image first, then use the "appleloader HD" command to switch to BIOS mode, it's much faster.

---

### Post by youbuntu on 2009-12-05
> **tom4everitt said:**
> I think it will always be EFI booting your mac, just like it will always be BIOS booting your pc (no matter if you have windows, linux or both on it). EFI is essentially the BIOS for macs (although it is much better and newer of course :) )

[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

I'm afraid I don't know many details about how it works, or what you can do to speed it up. Perhaps dear Google has an idea?

Yes, but I think the EFI is software on the EFI partition, not in firmware; could be wrong. Selling this Mac mini to buy a suitable priced Phenom II based PC, anyway.

Thanks :)

---

