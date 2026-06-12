---
title: "Nas,print server C7 1ghz thin client"
date: 2011-06-18
forum: Any Other OS
---

### Post by moh2010 on 2011-06-18
Hi,

I need some help.I have Thin Client 1Ghz Via C7 processor  with 256mb ddr2 ram expandable to 2 gb.I want to make it nas and printer  server with 1tb harddisk, attach to share among 2 to 3 people maX.


I know about freenas and openfiler

[http://www.freenas.org/category/version-comparison](http://www.freenas.org/category/version-comparison)

[http://www.openfiler.com/products/system-requirements](http://www.openfiler.com/products/system-requirements)

These seem to be to high spec,there are many small Nas hubs in the market,so I am sure there must some low powered Nas OS.

Oh! at the moment I have a cf card or usb so I will have to install embedded version.

On a side note,dose anyone know where can I buy 4gb microdrive which can be used instead CF,they were used in Ipod mini.

thanks

---

### Post by handy on 2011-06-19
I've used FreeNAS for some time in the past. It never let me down as a NAS. I didn't use it as a print server so I can't comment on that, though their wiki would certainly cover it.

FreeNAS is happy to boot from compact flash. I used an old 2GB drive that I has laying around.

These days I use a ReadyNAS Duo, as it uses so much less power than the box I used previously with FreeNAS.

---

### Post by Roasted on 2011-06-21
FreeNAS works very well on old hardware, as long as you don't use ZFS. Once you fire up ZFS it needs a ton of RAM to function. Likewise, FreeNAS seems to have a Samba bug when you're writing from a Linux system. I had a cap of 575 files on my CIFS share before I received Invalid Argument. Many hours of testing and many conversations with Samba developers confirmed it was an issue with FreeNAS 8. Despite that, it's still solid. But I just keep it simple and stable and stick to Linux on my NAS. It has yet to fail me.

---

