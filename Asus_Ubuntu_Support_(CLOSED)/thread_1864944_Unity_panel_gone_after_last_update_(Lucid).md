---
title: "Unity panel gone after last update (Lucid)"
date: 2011-10-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by terwilligerjones on 2011-10-19
Any idea why Unity3d would stop working on my Asus Eeepc 1005HA after the last upgrade? It's not that I'm shot in the head with Unity (I don't like it a bit), but I am used to it on this netbook, and I'm puzzled why it suddenly stopped showing the panel. Gnome seems to work fine, as does Unity2d.

Specs are:

slb_release -a
NoLSB Modules are available
Description Ubuntu 10.04.3 LTS

uname -a
Linux ASUS-netbook 2.6.32-35-generic #78 Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 Gnu/Linux

---

### Post by redoscar3 on 2011-10-19
More than likely you are affected by an xserver bug that a number of Lucid users are experiencing.  It killed my compiz desktop effects last night after I updated my system.  Found a fellow user that downgraded the two xserver packages to the previous version and it fixed the problem for now.  I'm guessing it might fix your problem as well.

If you can get to a terminal, use the following commands to downgrade the offending packages.

```
sudo aptitude install xserver-common=2:1.7.6-2ubuntu7
```

and

```
sudo aptitude install xserver-xorg-core=2:1.7.6-2ubuntu7
```

Thank user DeGrijze for this temporary fix.

Good luck,

Red

---

### Post by terwilligerjones on 2011-10-19
Ding! Ding! Ding! No more calls, we have a winner. Downgrading xserver did the trick. You don't perhaps know the xserver bug #, do you?

---

### Post by redoscar3 on 2011-10-20
Here's the Launchpad bug report for the Lucid xserver problem we are all experiencing:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)

From what the report is saying this morning, it looks as if they have found the problem and issued a fix for the regression.

Hope this resolves your Unity3D issues completely.

Red

---

