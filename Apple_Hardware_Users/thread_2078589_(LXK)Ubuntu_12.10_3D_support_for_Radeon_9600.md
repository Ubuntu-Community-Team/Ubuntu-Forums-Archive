---
title: "(L/X/K)Ubuntu 12.10: 3D support for Radeon 9600?"
date: 2012-10-31
forum: Apple Hardware Users
---

### Post by xeno74 on 2012-10-31
Does Ubuntu 12.10 have 3D support for the Radeon 9600 graphics card?

If yes than does [SuperTuxKart 0.7.3 PPC]("http://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.7.3/supertuxkart-0.7.3-linux-glibc2.7-ppc.tar.bz2/download") run on Ubuntu 12.10?




Screenshot by SuperTuxKart on Ubuntu 9.10 PowerPC with Radeon 9600 3D support:

/ * Click on the image to obtain a greater resolution * /

[[IMG]http://www.supertuxkart.de/stk07ubuntu910ppc-thumbnail.png[/IMG]]("http://www.supertuxkart.de/stk07ubuntu910ppc.png")

---

### Post by powerpcliberation on 2012-10-31
12.10 is still getting issues worked out and graphics is one of them in more ways than one.  I recommend you go with Lubuntu 12.04 instead.  It's very fast and stable.

You are also really limiting your linux progress and personal security by running that old 2.6 kernel.  The current kernel is 3.5 so you are missing out on all the improvements that happened between 2.6 and 3.5.

---

### Post by xeno74 on 2012-10-31
Hi powerpcliberation,

thanks for your answer :smile:

> **powerpcliberation said:**
> I recommend you go with Lubuntu 12.04 instead.  It's very fast and stable.


Does it have 3D support for my Radeon 9600 graphics card?

Cheers,

Xeno

---

### Post by powerpcliberation on 2012-10-31
> **xeno74 said:**
> Hi powerpcliberation,

thanks for your answer :smile:

Does it have 3D support for my Radeon 9600 graphics card?

Cheers,

Xeno


Give [this config file]("http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx") a try for 3D acceleration.  I never game on Linux and use a very graphically minimal GUI but I know of several that have successfully enabled #d on PowerPC.  I have no direct experience with this but I do know for a fact that it's certainly possible.

I use 12.04 with 3 different Radeon (9800/9000/7000) and all work fine but #d is normally never enabled by default.

---

