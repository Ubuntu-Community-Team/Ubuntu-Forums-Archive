---
title: "Wireless connection broke with upgrade"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by chajuram on 2007-02-17
Hi,

Till a few days back I was running everything successfully with the following kernel

> 2.6.17-10-generic

Recently with one of the automatic update (top right corner, upgrades available section). I see that when I log in to "2.6.17-11-generic" the wireless card is no longer displayed in the "Network Settings". Also not displayed in the results of "ifconfig".

Will appreciate any help.

Chajuram.

---

### Post by Kateikyoushi on 2007-02-17
Which wireless driver do you use ? Probably it is not loaded.

---

### Post by mikewhatever on 2007-02-17
It can be the linux-restricted for 2.6.17-11. They are not installed with the kernel upgrade, so if you had those restricted modules installed for 2.6.17-10 kernel, search for the new ones in synaptic and install them too.

---

