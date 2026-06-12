---
title: "[SOLVED] Question about installing *without* swap partition?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by sd_smoker on 2007-12-21
I've found lots of good info on swap partitions/files on this site but I still have a very basic question I can't seem to find the answer to. If I opt to use a swap file rather than a swap partition, will Ubuntu know what to do if there is no swap partition available upon install? Will it automatically use a swap file (or no swap) or will it bomb because it expects a swap partition by default?

---

### Post by Bruce M. on 2007-12-21
> **sd_smoker said:**
> I've found lots of good info on swap partitions/files on this site but I still have a very basic question I can't seem to find the answer to. If I opt to use a swap file rather than a swap partition, will Ubuntu know what to do if there is no swap partition available upon install? Will it automatically use a swap file (or no swap) or will it bomb because it expects a swap partition by default?

Ubuntu can use a "swap file" if you want.

Information on how can be found [[COLOR="Green"]here[/COLOR]]("http://packages.ubuntu.com/feisty/admin/dphys-swapfile")

And a very hand search tool for Ubuntu - [[COLOR="Green"]Ubuntu Search Engine[/COLOR]]("http://crunchbang.org/ubuntu-search-engine/")

If this solves your problem, please mark the thread "Solved" - "Thread Tools" pull down menu

Have a Great Day
Bruce

---

### Post by chris200x9 on 2007-12-21
I didn't do a swap the install uses around 512 ram so if it exceeds your physical ram during installtion it uses swap but if you have over 512 I wouldn't worry about it. IMO

---

### Post by sd_smoker on 2007-12-21
> **Bruce M. said:**
> Ubuntu can use a "swap file" if you want.

Information on how can be found [[COLOR="Green"]here[/COLOR]]("http://packages.ubuntu.com/feisty/admin/dphys-swapfile")

And a very hand search tool for Ubuntu - [[COLOR="Green"]Ubuntu Search Engine[/COLOR]]("http://crunchbang.org/ubuntu-search-engine/")

If this solves your problem, please mark the thread "Solved" - "Thread Tools" pull down menu

Have a Great Day
Bruce

Yep! The first paragraph states "Instead install without swap partition and then run this...", which tells me that installing without a swap partition won't cause any problems. Thanks!

---

### Post by chris200x9 on 2007-12-21
I do not know about that...sorry I cannot be of more help

---

### Post by Bruce M. on 2007-12-21
> **sd_smoker said:**
> Yep! The first paragraph states "Instead install without swap partition and then run this...", which tells me that installing without a swap partition won't cause any problems. Thanks!

More than welcome.  Glad to have helped.
Bruce

---

