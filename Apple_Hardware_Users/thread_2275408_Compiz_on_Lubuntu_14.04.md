---
title: "Compiz on Lubuntu 14.04"
date: 2015-04-25
forum: Apple Hardware Users
---

### Post by rican-linux on 2015-04-25
Well I got Compiz working on my iBook G4 running Lubuntu 14.04. You need to patch mesa to get the r300 driver working. (see the ubuntu-mate 14.04 release notes for the link to patched package). Then install the following:

```
rican-linux@ibookG4-lubuntu:~$ dpkg -l |grep compiz
ii  compiz                                  1:0.9.11.3+14.04.20150313-0ubuntu1    all          OpenGL window and compositing manager
ii  compiz-core                             1:0.9.11.3+14.04.20150313-0ubuntu1    powerpc      OpenGL window and compositing manager
ii  compiz-fusion-bcop                      0.8.4-1.1                             all          Compiz Fusion option code generator
ii  compiz-gnome                            1:0.9.11.3+14.04.20150313-0ubuntu1    powerpc      OpenGL window and compositing manager - GNOME window decorator
ii  compiz-plugins                          1:0.9.11.3+14.04.20150313-0ubuntu1    powerpc      OpenGL window and compositing manager - plugins
ii  compiz-plugins-default                  1:0.9.11.3+14.04.20150313-0ubuntu1    powerpc      OpenGL window and compositing manager - default plugins
ii  compiz-plugins-extra                    1:0.9.11.3+14.04.20150313-0ubuntu1    all          transitional dummy package.
ii  compiz-plugins-main                     1:0.9.11.3+14.04.20150313-0ubuntu1    all          transitional dummy package.
ii  compiz-plugins-main-default             1:0.9.11.3+14.04.20150313-0ubuntu1    all          transitional dummy package.
ii  compizconfig-settings-manager           1:0.9.11.3+14.04.20150313-0ubuntu1    all          Compiz configuration settings manager
ii  libcompizconfig0                        1:0.9.11.3+14.04.20150313-0ubuntu1    powerpc      Settings library for plugins - OpenCompositing Project
ii  python-compizconfig                     1:0.9.11.3+14.04.20150313-0ubuntu1    powerpc      Compizconfig bindings for python

```

Most of the plugins work, the cube works, but the 3D cube does not. See some screenshoot below

[ATTACH=CONFIG]261560[/ATTACH][ATTACH=CONFIG]261561[/ATTACH]

---

