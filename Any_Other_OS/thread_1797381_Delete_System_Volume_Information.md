---
title: "Delete System Volume Information"
date: 2011-07-05
forum: Any Other OS
---

### Post by xtheunknown0 on 2011-07-05
Hello,

When using Ubuntu, I want to delete the System Volume Information folder on my Windows XP partition on the same disk. It occupies ~29 GB out of the 40 GB of the disk. Will Windows still work?

I suspect that malware has infected the Windows partition, but I don't want to do any sort of scanning if no data worth backing up (on Windows) actually resides in the 'SVI' folder (why scan through the 29 GB?)

xtheunknown0

---

### Post by An Sanct on 2011-07-05
System Volume Information is, like the name says - a system folder and normally not accessible.

It contains things like *restore points*, *Link tracking services* (for .lnk repair,...), *Volume Shadow copy* information and potentialty a *WinFS database*.

**Removing this folder might render your Windows OS unusable!**

But, this is the nice thing about dual-booting :) Rename the folder first and try using windows, if it won't die or act strange, then consider deleting the folder again.

(You should also disable thumbnail caching, indexing and some other services. Also disable restore points...)

---

