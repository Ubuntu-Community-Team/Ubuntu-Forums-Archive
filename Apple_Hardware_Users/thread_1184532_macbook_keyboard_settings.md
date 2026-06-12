---
title: "macbook keyboard settings"
date: 2009-06-11
forum: Apple Hardware Users
---

### Post by ringo999 on 2009-06-11
Trying to get German keyboard working on macbook (1.1) with xubuntu jj, tried all kinds of model/layout combinations, also manually edited xorg.conf but no success, AltGr (right apple key) just not working... any idea?

See orgiginal post in [http://ubuntuforums.org/showthread.php?p=7438287#post7438287](http://ubuntuforums.org/showthread.php?p=7438287#post7438287)

Cheers
ringo999

---

### Post by cyberdork33 on 2009-06-11
they layouts are really not up to par for international apple keyboards. This is really unfortunate. There were many bugs about this, but I think they have all been combined under this one:
[https://bugs.edge.launchpad.net/mactel-support/+bug/67188](https://bugs.edge.launchpad.net/mactel-support/+bug/67188)

---

### Post by ringo999 on 2009-06-12
yes, looks like a bug, to bad it took me almost two days to figure out a workaround... from Debian I was used to control keyboard settings in xorg.conf but now I had to mess with xkb...

Check my original post for a workaround, shouldn't be to hard to fix the code in the original source.

[http://ubuntuforums.org/showthread.php?p=7438287#post7438287](http://ubuntuforums.org/showthread.php?p=7438287#post7438287)

Peace
Ringo999

:popcorn:

---

### Post by cyberdork33 on 2009-06-12
> **ringo999 said:**
> yes, looks like a bug, to bad it took me almost two days to figure out a workaround... from Debian I was used to control keyboard settings in xorg.conf but now I had to mess with xkb...

Check my original post for a workaround, shouldn't be to hard to fix the code in the original source.

[http://ubuntuforums.org/showthread.php?p=7438287#post7438287](http://ubuntuforums.org/showthread.php?p=7438287#post7438287)

Peace
Ringo999

:popcorn:

Might be good to mention that workaround in the bug report if it is not already there.

---

