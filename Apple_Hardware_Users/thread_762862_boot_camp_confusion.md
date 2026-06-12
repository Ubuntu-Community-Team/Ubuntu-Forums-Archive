---
title: "boot camp confusion"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by niteblind on 2008-04-22
HI all,

I am trying to triple boot my mac book and i think I might have missed a step somewhere. I currently have linux running ont he macbook but I cannot figure out boot camp.

Ecerytime I open boot camp it simply says that it cannot run on my primary mac os x partition and close down again.

I just tried loading from the apple install cd but boot camp is not on there.

now the only thing i may have done wrong is that in my haste to originally set up ubuntu I have already partitioned the hard drive would this be why boot camp is not working?

Any assistance would be appreciated.

niteblind

---

### Post by niteblind on 2008-04-22
anyone got any suggestions?

---

### Post by cyberdork33 on 2008-04-22
> **niteblind said:**
> now the only thing i may have done wrong is that in my haste to originally set up ubuntu I have already partitioned the hard drive would this be why boot camp is not working?yes, that's right. Bootcamp will not work if you have a linux partition. You don't need bootcamp though, boot the Ubuntu LiveCD and start the partition editor (gparted).

---

### Post by bluefish86 on 2008-04-22
To elaborate on what cyberdork said, once you have your partitions set up, all you need to do is boot off a windows CD and run the installer on the correct partition.  No boot camp required.

---

