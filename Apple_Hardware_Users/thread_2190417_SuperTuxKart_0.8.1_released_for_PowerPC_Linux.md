---
title: "SuperTuxKart 0.8.1 released for PowerPC Linux"
date: 2013-11-27
forum: Apple Hardware Users
---

### Post by xeno74 on 2013-11-27
We are proud to announce the release of SuperTuxKart version 0.8.1 for PPC Linux.

This release includes the following features:
* New track 'STK Enterprise'
* Updated tracks 'Old Mine', 'Around the Lighthouse' and 'Zen Garden'
* New modes 'Soccer' and 'Egg Hunt'
* New karts 'Xue' and 'Sara'
* Updated 'Beastie' kart
* Added tutorial
* Added new 'SuperTux' difficulty
* New bubblegum shield defensive weapon
* New combined speedometer and nitro meter
* Added ability to filter add-ons
* Updated nitro models
* Added ability to save and resume Grand Prix
* Improved skid marks and particle effects


It  has taken us a rather long time for a minor release, but most of the  developers have been rather busy with mentoring students for the &#8220;Google  Summer of Code 2013&#8221;. On the other hand, we had many contributions from  new developers: Dawid Gan tirelessly fixed bugs, making 0.8.1 the minor  release with most bug fixes. Johannesr1 added shield functionality to  bubblegum. Xenux added filtering of add-ons, Glenn De Jonghe saving of a  Grand Prix (just abort a Grand Prix at the beginning of a race, later  then restart the same Grand Prix again). Funto and Mohammad Al-Ghannam  added a multi-player soccer mode.

Download: [supertuxkart-0.8.1-altivec-linux-glibc2.13-ppc.tar.gz]("http://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.8.1/supertuxkart-0.8.1-altivec-linux-glibc2.13-ppc.tar.gz/download")

**Linux-PPC requirements:**


[LIST]
[*] Apple Power Mac G5 (Early 2005) with NVIDIA GeForce 6800 Ultra DDL (256 MB AGP 8x) or Radeon X850 XT (256 MB AGP 8x) 
[*] Apple Power Mac G5 (Late 2005) with GeForce 6600 (256 MB PCIe  x16), GeForce 7800 GT (256 MB PCIe x16), Quadro FX 4500 (512 MB PCIe  x16) 
[*] A-EON AmigaOne X1000 with AMD Radeon HD 4000, 5000, or 6000 Series (PCIe x16) 
[*] YDL PowerStation with ATI X1650 PRO (512 MB PCIe x16) 
[/LIST]

Ubuntu 12.04 PPC with Gallium 0.4 or higher
 
SuperTuxKart 0.8.1 official video: [http://youtu.be/WutAN4i98_o](http://youtu.be/WutAN4i98_o)

SuperTuxKart 0.8.1 official poster: [OfficialPoster_081.jpg]("http://supertuxkart.sourceforge.net/persistent/images/6/65/OfficialPoster_081.jpg")

[IMG]http://supertuxkart.sourceforge.net/persistent/images/thumb/6/65/OfficialPoster_081.jpg/424px-OfficialPoster_081.jpg[/IMG]

We hope you enjoy the new release, and as always we  welcome new artists and programmers to join us, either through our  forum or our mailing list. Also, you can follow us at Twitter  @supertuxkart.


STK Development Team

---

### Post by xeno74 on 2013-11-28
Hi all,

        I've released a bug fix version of the static Linux AltiVec package. The reason was that the bluetooth lib has a dependency to glibc 2.15. Therefore, it doesn't run on Debian 7 and MintPPC 11. I've compilied the static version of the bluetooth lib into the STK binary. And now it runs on Debian 7 and MintPPC 11 with glibc 2.13.
Additional I have released a version for older Linux systems with glibc 2.11.1 or higher without AltiVec optimization. This version runs also on the Cyrus boards in the future.

Downloads:

[supertuxkart-0.8.1-2-altivec-linux-glibc2.13-ppc.tar.gz]("http://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.8.1/supertuxkart-0.8.1-2-altivec-linux-glibc2.13-ppc.tar.gz/download")

[supertuxkart-0.8.1-linux-glibc2.11.1-ppc.tar.gz]("http://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.8.1/supertuxkart-0.8.1-linux-glibc2.11.1-ppc.tar.gz/download")

All the best,
       Christian

---

