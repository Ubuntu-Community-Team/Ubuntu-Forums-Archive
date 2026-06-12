---
title: "Phosphor screensaver"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by cwhisperer on 2008-02-04
I'm using kde3.5 and I want to run the phosphor screensaver, but it does not appear in the screensavers list. What do I need more, I already have installed everything from xscreensaver available? Thanks for you help

---

### Post by kaiju on 2008-02-16
just a suggestion, i don't know if this will help you at all, but let's hope so :)
running
```
apt-cache search xscreensaver --names-only
``` and
```
apt-cache search kscreensaver --names-only
```
gives the following lists:

xscreensaver - Automatic screensaver for X
xscreensaver-data - data files to be shared among screensaver frontends
xscreensaver-gl - GL(Mesa) screen hacks for xscreensaver
xscreensaver-data-extra - data files to be shared among screensaver frontends
xscreensaver-gl-extra - GL(Mesa) screen hacks for xscreensaver

and

kscreensaver - additional screen savers released with KDE
kscreensaver-xsavers - KDE hooks for standard xscreensavers
kscreensaver-xsavers-extra - KDE hooks for standard xscreensavers
kscreensaver-xsavers-webcollage - webcollage screensaver KDE hook

are you sure you've tried all these packages?

---

