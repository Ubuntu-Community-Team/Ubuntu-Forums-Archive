---
title: "Wrong colors with Mesa 9.2 and Mesa 10.0 on Lubuntu 13.10"
date: 2013-12-20
forum: Apple Hardware Users
---

### Post by xeno74 on 2013-12-20
[IMG]http://www.mesa3d.org/gears.png[/IMG]

Hi all,

I've tried Mesa **9.2.2-1** and **10.0.0-1** on Debian **Sid** and Lubuntu **13.10**.
Unfortunately both have issued false colors in games. They appear to be ABGR
instead of RGBA, thus blue becomes green, red becomes alpha etc.

Mesa **8.0.5-4** and Mesa **9.1.6** have _no_ color problem.

I've created a bug report on freedesktop.org.

Bug report **72877**:

[https://bugs.freedesktop.org/show_bug.cgi?id=72877](https://bugs.freedesktop.org/show_bug.cgi?id=72877)
[http://lists.freedesktop.org/archives/mesa-dev/2013-December/050363.html](http://lists.freedesktop.org/archives/mesa-dev/2013-December/050363.html)

The transitional solution is to install the old Mesa 8.0.X with "Force Version"
with the Synaptic package manager on new distributions.

Hardware:

AmigaOne X1000 (Nemo)
PA Semi Dual-core PA6T-1682M, 1.8GHz PowerISA™ v2.04+ CPU
"Xena" 500MHz XMOS XS1-L2 124
8GB DDR2 SDRAM
HIS Radeon HD 6870, 1 GB RAM
OCZ600MXSP 600 Switching power supply
RTL 8139/8139C/8139C+ network card
TSSTcorp CDDVDW SH-224BB dvd drive
ATA ST2000DM001-9YN1 SEAGATE HD
ATA ESA 3SF1240GB HD

More information: 

[http://en.wikipedia.org/wiki/AmigaOne_X1000](http://en.wikipedia.org/wiki/AmigaOne_X1000)
[http://www.supertuxkart-amiga.de/amiga/x1000.html](http://www.supertuxkart-amiga.de/amiga/x1000.html)

Rgds,
Christian

---

### Post by xeno74 on 2014-01-07
Hi,
    
    I have installed the development branch of Lubuntu 14.04 PowerPC. It works     but with wrong colors in games (see bug report:     [https://bugs.freedesktop.org/show_bug.cgi?id=72877](https://bugs.freedesktop.org/show_bug.cgi?id=72877)). 

[ATTACH=CONFIG]249290[/ATTACH]

The x86 version hasn't the problem with the wrong colors.

[ATTACH=CONFIG]249291[/ATTACH]

Rgds,
Christian

---

### Post by pauljwells on 2014-01-14
I wrote a patch some time ago for Unity-2D on PPC. Might be useful...

[http://ubuntuforums.org/showthread.php?t=1750119&p=10772531#post10772531]("http://ubuntuforums.org/showthread.php?t=1750119&p=10772531#post10772531")

---

