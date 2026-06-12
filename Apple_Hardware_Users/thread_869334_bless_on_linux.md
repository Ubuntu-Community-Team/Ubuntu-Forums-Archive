---
title: "bless on linux"
date: 2008-07-24
forum: Apple Hardware Users
---

### Post by Nosferax on 2008-07-24
Hey, has anyone compiled the bless utility (from OSX) on his linux machine?

 I know apple made the source code available for download on one of their repositories but when I downloaded it I realized there was only a XCode project file so I gave up there. Sooo I was just wondering if anyone had done anything with that, since it's a pretty useful tool to have around when you don't care about OSX and want to avoid booting into it at all costs :P

---

### Post by stream303 on 2008-07-25
If you are talking ppc, you may want to take a look at ybin and/or mkofboot, which is part of the ppc distro.  We use it all the time to bless the drives to get them to boot.

---

### Post by kosumi68 on 2008-07-25
For intel macs, I believe it is being worked on. The kernel EFI support has been flaky at best, but there are new patches applied in the upcoming Intrepid release. Worth trying again then, I suppose.

---

### Post by cyberdork33 on 2008-07-25
Does anyone know where the project pages for these new tools might be? I think blessing is a bit different in Intel Macs than the PPC Macs since you are essentially marking something as bootable for the EFI system.

---

