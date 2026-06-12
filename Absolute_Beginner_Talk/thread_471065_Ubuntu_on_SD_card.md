---
title: "Ubuntu on SD card"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by thevenerablez on 2007-06-11
Hi,

I have a Fujitsu LifeBook. It has a built-in SD card slot. Can I install Ubuntu onto a 4GB SD card and run it off that? Has anyone had any success doing that?

Thanks.

---

### Post by phr0ze on 2007-06-11
I guess its possible if your lifebook will boot that device. If not, I doubt grub will recognise the slot at that point. I have a lifebook too, I should try it but I dont have a 4GB card laying around.

---

### Post by cotcot on 2007-06-11
Can you select the cardreader to boot from in bios ? If yes, you can.

---

### Post by insane_alien on 2007-06-11
probably yeah. you might need to put a boot partition on the HDD if you can't boot from the card reader but the rest of the filesystem can be on the card reader.

---

### Post by thevenerablez on 2007-06-11
Why would I need to add a boot partition to my HDD for the SD card slot but not an external hard drive? I can run Ubuntu on my external hard drive just fine, but I am looking for something more portable.

Thanks.

---

### Post by johnny4north on 2007-06-11
have you considered installing to a usb stick($40.00 for 4gig)? - [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) :)

---

### Post by insane_alien on 2007-06-11
> **thevenerablez said:**
> Why would I need to add a boot partition to my HDD for the SD card slot but not an external hard drive? I can run Ubuntu on my external hard drive just fine, but I am looking for something more portable.

Thanks.

only if you can't boot directly from the card reader. all depends on the BIOS

---

### Post by csls1231 on 2007-12-30
perhaps not the most intelligent questions but can anyone please advise:

1. how to find out on my system (Dell Latitude D420) whether BIOS support is available for booting from SD card?

2. will I not need afterwards appropriate linux driver(s) for the SD card so that it is recognised ? [please ignore this if it is too dumb a question]

3. between SD and CF, which one you think would be better (for speed and durability) ? because, as an alternative, I am also considering running Linux from CF card fixed on the PCMCIA port [although i still do not know if that is at all possible].

any suggestion would be greatly appreciated.
Thanks

---

### Post by ceeleelewis on 2008-01-16
Is there a tutorial on how to get a bootable image on to sd? i can't boot from usb stick on this stupid toshiba m200. For some reason it wil not boot from the external cd . So the only option at this point is a bootable sd installation.

---

