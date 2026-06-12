---
title: "Memory usage in PC-BSD?"
date: 2008-03-10
forum: BSD
---

### Post by JonUK76 on 2008-03-10
Hi, I recently installed PC-BSD on to one of my systems. Something I wanted to query was the memory usage. Specifically, when I first start the system up, if I bring up the KDE System Guard it shows about 300mb memory used, 700-ish free.

If I then leave it running for some time, maybe open up and close down a few programs or whatever, there have been occasions when I've gone into KDE System Guard and it appears that very little memory is free, even though no actual applications are running. Checking the processes that are running, there seems to be a lot of memory used up by various kdeinit processes, amongst many other things.

I've searched over the PCBSD forums and found someone else mentioning this and they gave some explanation about BSD showing free memory differently from Linux? I didn't really understand the explanation.

What I want to know really is, is this behaviour normal for PC-BSD or FreeBSD in general?

Thanks

---

### Post by mips on 2008-03-11
The memory is cached, the same as in linux if I'm not mistaken.

---

### Post by JonUK76 on 2008-03-16
> **mips said:**
> The memory is cached, the same as in linux if I'm not mistaken.

I understand that but it still doesn't really make sense to me.

For example, I am currently in Ubuntu and typing this on Firefox. The system has been on for the last 24 hours or so and in that time I have edited a few documents in OpenOffice, watched a couple of videos in VLC, as well as browsing a few hundred pages in Firefox. The Gnome System Monitor is currently showing 339mb of memory is used, with no swap.

On my system running PC-BSD it starts off with about 300mb being used (as shown in the KDE system monitor), but after being on for 5 or 6 hours, and doing stuff like the above, memory usage creeps up to the 900mb mark, even when everything has been closed down afterwards. It also seems to become less responsive than when it first started. E.g. clicking the K Menu seems to have a delay before it opens.

---

### Post by cammin on 2008-03-16
I'd bet it has to do more with KDE than BSD.

Also, I don't think Gnome shows memory being used as cache.

---

