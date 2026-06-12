---
title: "can't compile evolution-rss plug-in"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by mattinthematrix on 2007-07-15
I'm trying to compile the evolution-rss-0.0.4 plugin on my powerpc based ubuntu 7.04.

When I './configure' it errors out because it says I don't have libsoup-2.2, but I actually do according to synaptic.

Overriding the pkg-config results in a make file that doesn't work either.

Any ideas?

Thanks!

---

### Post by ramjet_1953 on 2007-07-15
Have you installed the [COLOR="Blue"]build-essential[/COLOR] package?

[COLOR="Red"]sudo apt-get build essential[/COLOR]


You will also need the [COLOR="Blue"]libsoup2.2-dev[/COLOR] package

[COLOR="Red"]sudo apt-get install libsoup2.2-dev[/COLOR]

Regards,
Roger :cool:

---

### Post by mattinthematrix on 2007-07-15
That's what I needed. Thanks!

---

