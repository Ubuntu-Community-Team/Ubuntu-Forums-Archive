---
title: "2Linux distro's &amp; 1 swap partition?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Zralou on 2008-04-07
I have Kubuntu installed on a second HDD, and now I want to install another distro on the same drive.  Will the Kubuntu swap partition serve both distro's, or do I need to partition for a second swap?

Sara Lou

---

### Post by Jerry N on 2008-04-07
Works for me.  I have a drive with both Ubuntu 7.10 and LinuxMint 4.0, single swap partition and single home partition.  When you install your second distribution, it should find the existing swap partition.

Jerry

---

### Post by Inxsible on 2008-04-07
When you do install the second distro, however, make sure that you select the same swap partition while you make partitions. Like Jerry said, it will find the existing swap, but you will still have to assign (mount) it as the one you want to use with your newer distro.

---

### Post by SOULRiDER on 2008-04-07
Not adding anything new here but yes, it works. Just make sure when you install you select the same swap partition or that if you accidentally create a new one you edit /etc/fstab acordingly.

---

### Post by Zralou on 2008-04-07
Thanks guys, that sounds painless enough.  I'll give it a try this weekend, hopefully without screwing up.

Sara Lou

---

### Post by Inxsible on 2008-04-07
> **Zralou said:**
> Thanks guys, that sounds painless enough.  I'll give it a try this weekend, hopefully without screwing up.

Sara LouGood Luck !! Let us know how it goes.

---

