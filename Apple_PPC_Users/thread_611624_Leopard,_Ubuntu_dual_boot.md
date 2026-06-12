---
title: "Leopard, Ubuntu dual boot"
date: 2007-11-13
forum: Apple PPC Users
---

### Post by sickdude on 2007-11-13
Hi all,

I have a ibook G4 with the 1,2 Ghz ppc and 1,25 GB ram in it.

So its a little old school but it works awesome.

Anyway i upgraded to Leopard last week and now im having alot of issues with the wireless network at school. If there is something i hate its network issues. 

So i want to fix myself a dual boot lappy with, of course, Ubuntu on another partition.

I did alot with dual boot setups in the past and i know how it works, but not on a mac. And not with Leopard.

So i was wondering if you guys have a little walktrough or some helpfull tips?

Is bootcamp a option or is that a intel/windows option only? 

Are there known issues with the G4 ibook that i should know of?

Anyways thanks in advance for the helpfull tips :-)

---

### Post by pxwpxw on 2007-11-13
> **sickdude said:**
> Hi all,

I have a ibook G4 with the 1,2 Ghz ppc and 1,25 GB ram in it.

So its a little old school but it works awesome.

Anyway i upgraded to Leopard last week and now im having alot of issues with the wireless network at school. If there is something i hate its network issues. 

So i want to fix myself a dual boot lappy with, of course, Ubuntu on another partition.

I did alot with dual boot setups in the past and i know how it works, but not on a mac. And not with Leopard.

So i was wondering if you guys have a little walktrough or some helpfull tips?

Is bootcamp a option or is that a intel/windows option only? 

Are there known issues with the G4 ibook that i should know of?

Anyways thanks in advance for the helpfull tips :-)

To install ubunu multibooting with Macosx should be simple (except for some post install Ubuntu 710 issues gradually being resolved)

1. resize your Leopard volume (partition) to leave a free space partition for ubuntu.
(optionally you might want to create an additional macos partition).

2. install ubuntu in the available free space. Selecting that option in the ubuntu installer partioning creates a small ~1MB Apple_Bootstrap partition, linux root and linux swap. Bootcamp is not used for powerpc booting.

Macosx HFS+ partitions can be resized from macosx (I dont have Leopard but I think it has a bootcamp GUI), or diskutil ResizeVoloume. Or friom the ubuntu Desktop install CD Gnome Partition Editor provided journalling is temporarily disabled in Macosx.

the only issue I had with ubuntu710 Desktop CD  on an iBookG4 1MHz with 768MB ram, was the need to choose the  "live-nosplash" option when booting the Desktop CD (as a live cd),
However I installed ubuntu710 by upgrading from 704.

---

