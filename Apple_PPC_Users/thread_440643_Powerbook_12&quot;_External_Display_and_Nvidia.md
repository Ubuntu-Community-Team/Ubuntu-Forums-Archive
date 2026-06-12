---
title: "Powerbook 12&quot; External Display and Nvidia"
date: 2007-05-11
forum: Apple PPC Users
---

### Post by zalberico on 2007-05-11
I'm trying to get my 12" Powerbook to connect to a 17" Dell Display.  When I connect it nothing happens and when I reboot the large display just remains white while the small one is fine.

My powerbook has the Nvidia GeForce FX Go5200 graphics card and I was wondering if and how you can install the drivers to get compiz/beryl up and running.  Currently when I select start desktop effects I just get a white screen.  When I check to see if 3D support is running I get Direct Rendering:No.

Thanks, any help is greatly appreiciated.

---

### Post by stmiller on 2007-05-11
DVI out is only supported on ATI cards for PowerPC Linux. And there is no 3D available for Nvidia cards under PowerPC Linux. There is an open source nvidia project that will have drivers very soon....

See the FAQ at the link below for more info:

---

### Post by APU on 2007-05-12
DVI does also work on Nvidia PowerBooks although you have to plug in the Monitor first, then push the Power button on the machine and quickly close the lid.

It will then boot up, using only the external (DVI or VGA) Monitor. You can then as well open the lid again to enable better cooling and prevent the internal LCD from getting too hot. The internal screen will stay disabled and you can use the external one.

Still, no 3D though - that means no Compiz or Beryl until Nouveau finishes the free drivers.

---

