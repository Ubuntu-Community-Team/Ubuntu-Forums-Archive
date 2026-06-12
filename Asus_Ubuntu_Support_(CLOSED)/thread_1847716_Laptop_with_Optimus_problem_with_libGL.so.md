---
title: "Laptop with Optimus: problem with libGL.so"
date: 2011-09-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by apetrelli on 2011-09-21
Hello,
I have an Asus Laptop N53S with NVidia Optimus, i.e. Intel 915 plus NVidia GEForce 540M. Kubuntu Natty.
Now I am able, through the use of Ironhide, both Intel chipset (default) and NVidia (via optirun command).

However I have a problem with DRI with Intel chipset: i see characters upside down, due to the problem described here:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/781353](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/781353)

The solution seems to be to uninstall NVidia driver, or to disable DRI, since the loader is getting the wrong libGL.so.

Now, is there a way to specify what libGL.so to get inside XOrg configuration?

---

