---
title: "Vista concerns"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2007-02-05
Two issues.

I have a laptop (brand new Intel Dual Core) with Vista.  I want to install Ubuntu on a new partition.  I know how, having done it on my AMD 4200 desktop which uses XP as well, using Gparted.  I'm traveling and am concerned that something might be different on Vista.

Second, I booted from UBUNTU Live Cd and did not see my wireless card, Broadcom using Windows driver 4.102.15.56 by WINDKK.  Is this something I can do from CD or do I need to install on hard drive first?

Reason for wanting to do this is that Vista and "STAYONLINE", a hotel connection provider seem to have issues.  I was told this after an unsuccessful hour and a half of phone time.

Thank you.

---

### Post by mikewhatever on 2007-02-05
There is a site on [Dual Booting Ubuntu and Vista]("http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx")

As pqueiro just pointed out below, Broadcom needs ndisrapper, which you probably know about.
There is [A PAGE ON BROADCOM](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29) in the community docs.

---

### Post by pqueiro on 2007-02-05
If memory serves, Broadcom cards need ndiswrapper to work - though I am not completely sure.

---

### Post by zgornel on 2007-02-05
> **pqueiro said:**
> If memory serves, Broadcom cards need ndiswrapper to work - though I am not completely sure.

Not all of them ofcourse. If it is not recognized at boot (no module loaded) use ndiswrapper or a newer kernel (if it supports the new card).

---

