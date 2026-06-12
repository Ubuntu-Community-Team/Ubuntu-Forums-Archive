---
title: "GRUB difficulties on iMac"
date: 2016-11-25
forum: Apple Hardware Users
---

### Post by Turon on 2016-11-25
Every time I try to install Ubuntu 16 it imposes it's grub menu and renders OS X booting impossible. I have to open up Internet recovery mode and select my OS X drive as my default boot option and I still can't access my Bootcamp Windows because the Mac's own built in boot manager is destroyed by the damn grub. I cloned rEFind to a little partition on the drive I wanted Ubuntu. I don't need grub, how do I remove it and get the Mac's boot menu back?

---

### Post by Turon on 2016-11-29
As it turns out the effects of Ubuntu 16 grub are not as destructive when upgrading from Ubuntu 14 to 16 which is what I did. I found all I needed to do in my case was open internet recovery mode and set the default boot option to OS X. holding alt to access the mac boot menu isn't actually effected then.

---

