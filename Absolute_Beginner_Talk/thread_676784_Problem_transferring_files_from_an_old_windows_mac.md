---
title: "Problem transferring files from an old windows machine"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-01-24
Hi, I did an install of Gutsy and was transferring about 10 gigs worth of files from a windows machine on a hard-wired network.

After about 5 minutes, the transfer locks up and it says "the specified resource could not be found".

Then, I have to cancel the transfer, but pretty much all the "networky" things under Ubuntu stop working.

I can't reach google, all of the network resources go away....

On the windows machine, everything works normally... so something has "tweaked" inside the ubuntu machine.

I was doing all of this before upgrading the packages... which I started this morning when I left for work, but I was wondering if anyone had seen anything similar?

What caused the problem?

---

### Post by peabody on 2008-01-24
You were using nautilus to copy the files I take it?

I've had bad luck with large data transfers using gnome-vfs.  The holy grail of accessing network shares in my mind is the fusesmb package.  Bit of a pain to setup, but I've found it to be much more transparent and reliable.

---

### Post by joesmith1234 on 2008-01-24
> **peabody said:**
> You were using nautilus to copy the files I take it?

I've had bad luck with large data transfers using gnome-vfs.  The holy grail of accessing network shares in my mind is the fusesmb package.  Bit of a pain to setup, but I've found it to be much more transparent and reliable.

Nautilus?

I just did drag and drop

---

### Post by peabody on 2008-01-24
Nautilus is Gnome's file manager, so yes, you used nautilus.

---

### Post by dsplabs on 2008-01-24
What network card are you using? Is it by any chance an old PCI 10 or 100 Mbit card? I have had problems with those... small files worked fine, large file transfers locked the networking all together. I experienced this on Fedora. With newer network cards no such problems. Very strange and very frustrating when it happens.

---

### Post by joesmith1234 on 2008-01-24
> **dsplabs said:**
> What network card are you using? Is it by any chance an old PCI 10 or 100 Mbit card? I have had problems with those... small files worked fine, large file transfers locked the networking all together. I experienced this on Fedora. With newer network cards no such problems. Very strange and very frustrating when it happens.

Yes, I believe it is a very old card.

The on board card wasn't supported in Ubuntu, so I had to go "digging".

---

