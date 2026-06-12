---
title: "How does Sorcerer do tarball patches?"
date: 2012-08-12
forum: Any Other OS
---

### Post by Splooshie123 on 2012-08-12
Sorcerer is a source-based distribution

Quoted from the Wikipedia article:
> When a new source is required and an older source was previously  downloaded, then Sorcerer will download a tiny patch that transforms the  old source tarball into a current source tarball.

I am just curious how this is possible. Sorcerer's website also mentions that it downloads source code straight from the source.

I get the impression that somehow a diff is generated over the internet without having to download the whole thing all over again. Having someone generate the diff would be impractical because the version of the old source is unknown. You would have to store diffs for updating 0.1 to 1.0, 0.2 to 1.0, etc.

So, is something like this (generate a diff of two files, one local, one remote) possible? And how would it be done?

---

### Post by jtarin on 2012-08-13
Here's a [link]("http://northtech.us/content/20100426/distrowatch-review-sorcerer-linux-including-installation-and-configuration") for....what I think....is a terrific insight into this OS. I hope it helps.

---

### Post by Splooshie123 on 2012-08-13
The article didn't have the answer I was looking for, but it did mention xdelta, which led me to a comparison of diff algorithms, which led me to [this Ph.D. thesis]("http://www.samba.org/%7Etridge/phd_thesis.pdf") which describes the rsync algorithm (page 49).

Close enough.

---

