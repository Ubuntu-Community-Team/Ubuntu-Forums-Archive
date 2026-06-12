---
title: "High Memory Usage"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ocho on 2007-04-24
I recently installed Sysinfo and discovered that Ubuntu is somehow using 750 mb of my ram without running anything that I would expect to use so much RAM: Rhythmbox, firefox, gaim, GDesklets, and Beryl. 

How can I check to see which programs are using up such a high amount of RAM?

My relevant specs are: AMD Athlon(tm) 64 Processor 3800+, 1gb DDR 800mhz dual channel RAM, NVIDIA Geforce 7600 GT 512 mb.

Thanks.

---

### Post by MRiGnS on 2007-04-24
linux also uses ram for system cache.

for example 22% of my ram are asigned to applications and 78% are used for caching.

---

### Post by ocho on 2007-04-24
Thanks for your extremely quick reply, MRiGnS.

Sysinfo actually doesn't count cached RAM as in use. It's showing 232 MB cached, 502 MB used, 198 inactive. This is less than before, but I still don't think my computer should be using so much RAM for so little...

---

### Post by MRiGnS on 2007-04-24
hit alt+f2 and run gnome-system-monitor

under the process-tab you can arrange the tasks according their memory usage.

---

### Post by ocho on 2007-04-24
Thanks again for the quick reply, that's just what I was looking for.

It seems Beryl is using about 256 mb RAM, which is to be expected I suppose, but what I didn't expect is that Azureus is using nearly 100 mb RAM. I guess I'll be switching to a new torrent manager...

---

