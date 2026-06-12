---
title: "&quot;deprecated PCMCIA ioctl usage&quot;?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by babysteps on 2007-07-30
Having just started to look in the dmesg, as I crawl towards wireless-surfing-dom (i don't think it's ever going to happen, really..I'm not ever going to get online with ANY wireless interfaces...) I noticed this message, and was wondering if someone can tell me what it is really saying. 

"
pcmcia: Detected deprecated PCMCIA ioctl usage.
pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
pcmcia: see http:..[www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details."

Then it's always followed by:

"cs: memory probe 0xa0000000-0xa0ffffff: clean.
hdb: tray open
end_request: I/O error, dev hdb, sector 4
Buffer I/O error on device hdb, logical block 2
hdb: tray open   "

I have not been opening my cd rom tray at all. Though, the cdrom and pcmcia are neighbors on my laptop.  

Can someone tell me what this is about. I went to the website it provided, but , it sort of went over my head what i was supposed to gather from this message.

Thanks..

babysteps

---

### Post by DBStevens on 2007-07-30
Yeah, it is saying that whatever you are doing isn't really being maintained any more so if you use it you are going to have problems which surprise you are actually having.

It also is telling you that there is a new way to handle this and you should upgrade to the newer methods.

Sounds like you have one part of your system that is out of step with another part.  Did you by any chance upgrade your kernel and not the PCMCIA tools? 

Beyond saying that I can't really help as I don't have any of said critters on my system.

---

