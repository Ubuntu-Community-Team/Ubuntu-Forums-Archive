---
title: "my story with PowerMAC G5"
date: 2004-12-07
forum: Apple PPC Users
---

### Post by replacement on 2004-12-07
i am quite happy now with ubuntu hoary (daily build) running on G5 ... even though i spent some time on it. here is what i did. hope it may be useful 

1. install ... the hardware detection won't detect the network interface module, but just go on. 
2. ubuntu doesn't boot after installation. it turned out yaboot.conf isn't set properly (i have two sata drives, and i installed ubuntu on sdb). so i had to boot up with gentoo-livecd (ppc64), mount the root partition and fiddled with yaboot.conf and such. 
3. now i can boot, and the rest is pretty much regular. 
4. enable network by modprobe sungem sungem_phy. these modules are apparently there but somehow not available during installation 

it was great! my last wish is to have hardware accelerated graphics working for nvidia card. anyone done that so far?

---

### Post by atom on 2004-12-20
until nvidia starts providing binary drivers for ppc/ppc64 in linux, you will not have 3d support on a g5.

---

### Post by Viro on 2004-12-21
[QUOTE=atom]until nvidia starts providing binary drivers for ppc/ppc64 in linux, you will not have 3d support on a g5.[/QUOTE]
 Or you can use a ATI card (Radeon 9200 and *below*).

---

### Post by humberto on 2004-12-21
[QUOTE=replacement]
2. ubuntu doesn't boot after installation. it turned out yaboot.conf isn't set properly (i have two sata drives, and i installed ubuntu on sdb). so i had to boot up with gentoo-livecd (ppc64), mount the root partition and fiddled with yaboot.conf and such. 
[/QUOTE]

Can you specify in more detail what you did? I couldn't boot from the Warty CD, got Array 1 booted, but after I finished the install was unable to get a working yaboot.conf.

I ended up installing Gentoo on the dual 2.5 GHz G5 to test out 64 bit compilation, but it's still a very experimental system.

---

