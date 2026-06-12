---
title: "Anyone with Gutsy on a 20&quot; Intel iMac yet?"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by ward83 on 2007-10-18
I'm currently upgrading to Gutsy, but it's going quite slow at the moment, presumably because the download servers are being hammered right now. Has anyone successfully installed or upgraded to Gutsy on a 20" Intel iMac? I'm hoping it will fix the issues I'm having with Feisty, which are:

- Wireless network card not working at all, I've even tried ndiswrapper
- No 3d acceleration, video card is a Radeon Mobility X1600

---

### Post by cyberdork33 on 2007-10-19
> **ward83 said:**
> - Wireless network card not working at all, I've even tried ndiswrapper
- No 3d acceleration, video card is a Radeon Mobility X1600
I have been running only Gutsy on my iMac since Tribe 5

Both of those things worked in feisty the same way you will have to get them working in gutsy, and that will not likely change soon. Your Wi-Fi is a Broadcom card, who does not release specs for linux drivers, and thus are not well supported by any driver. ndiswrapper works with some dell drivers or the drivers from Boot Camp.

The video card requires a closed-source, proprietary driver to get 3D acceleration working. The restricted drivers manager should prompt you to install this.

---

