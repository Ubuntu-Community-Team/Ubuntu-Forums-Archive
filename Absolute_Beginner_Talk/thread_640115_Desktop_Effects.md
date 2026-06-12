---
title: "Desktop Effects"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by dgoodma on 2007-12-13
Getting stuck on trying to enable Desktop Effects.

My ATI video drivers are all up to date, and seem to be working. Mobility Radeon X1600.

When I try to enable Desktop Effects, it says The Composite Extension is not available.

I installed the CompizConfigSettings, ccsm, checked a bunch of stuff, nothing complains, but don't seem to be getting any effects. The Enable Desktop Screen will not let me select Custom, as it complains about that Composite Extension. Where is that, how do I get it?

In the /etc/X11/xorg.conf it shows:
Section "Extensions"
        Option          "Composite"     "0"


Does that have to be "1" ?

---

### Post by Thanoulis on 2007-12-13
Not quite. Delete the "0" entry and add "Enable".
That worked for me.;)

---

### Post by MrFSL on 2007-12-13
Not trying to troll... but seriously everyone... you can get answers much faster by searching first.

This forum..

And the ubuntu wiki: [http://wiki.ubuntu.com](http://wiki.ubuntu.com)

And the online help documentation: [http://help.ubuntu.com](http://help.ubuntu.com)

Here is your answer:
[https://help.ubuntu.com/community/CompositeManager/CompizFusionATI](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI)

---

### Post by dgoodma on 2007-12-13
Thanks, I did search, but did not find what you did, hence the posting here....
And now everything works.
Seems like this process should be a little more automatic, but I guess it is because of a newer laptop with proprietary drivers.
Keeps us newbies wandering around.

---

