---
title: "Improve Laptop Graphics"
date: 2008-12-18
forum: Arch and derivatives
---

### Post by AlbaTiVo on 2008-12-18
Hi all,

I have been using Ubuntu for a couple of years now, but looking to improve the speed of my ageing laptop I found myself in this forum. I was impressed with everyone's enthusiasm for Arch and made the switch this weekend.

So far I love the speed difference - everything is much "snappier" :)

The only issue I am having to date is in getting the ATI Rage Mobility P/M AGP 2x video card working with any driver other than the Vesa driver.

When I change the driver from "vesa" to "ati" I get a message saying "Failed to load module "mach64" (module does not exist, 0)"

I have searched on here and on the Arch forums, but have not been able to find a solution that works. Any ideas?

Steven

---

### Post by cammin on 2008-12-18
Install the **xf86-video-mach64** driver through Pacman.

---

### Post by AlbaTiVo on 2008-12-19
That worked a treat - thank you very much!

---

