---
title: "Panic! due to half installed graphics drivers"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-12-06
Hi all,

I am trying to install the openchrome drivers for my laptop (it has cle266 graphic chip) running xubuntu 7.10. I tried synaptic to install them but got nowhere so found the following guide for compiling and installing the drivers:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

The openchrome 2d drivers compiled and installed with no problems however only half the 3d drivers seem to compile.

The guide states that 3d should work in edgy (so i assumed also in gutsy) and if not to follow the rest of the guide.

"libdrm" compiled and installed but "drm kernel modules" won't compile.

This command "make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via" gives the following message;

cmp: invalid option -- r

any suggestions would be welcome as I don't want to turn the computer off because with only half the new drivers the graphics may not work when it turns back on (I can revert an xorg.conf etc from the recovery console but I am not confident enough to be able to follow a guide and start messing about compiling stuff)

Many thanks

---

### Post by V-600 on 2007-12-06
Possibly in my ignorance i decided to plough on regardless (at the least it will be a learning experience).

I changed the command to:

make LINUXDIR=/lib/modules/2.6.22-14-generic/build DRM_MODULES=via

it compiled and I was able to follow the rest of the guide but i still have no 3d acceleration.

Thats another issue though.

---

