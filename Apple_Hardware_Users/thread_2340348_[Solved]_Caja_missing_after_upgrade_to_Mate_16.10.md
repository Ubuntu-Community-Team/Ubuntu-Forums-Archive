---
title: "[Solved] Caja missing after upgrade to Mate 16.10"
date: 2016-10-17
forum: Apple Hardware Users
---

### Post by apple-apple on 2016-10-17
Ok, so I upgraded my Ubuntu Mate install to 16.10 from 16.04. I had problems installing 16.10 from disk though. I attempted to follow ernsteiswuerfel's advice and just create an ext2 boot partition to get around the bug (installer messes up the partition scheme)  				 				 					 						 	but I'm just not that good. I kept messing up. So I just re-installed 16.04 and upgraded. It completed but with some errors. One of which was that caja couldn't be installed. It was there in synaptic, but couldn't install due to some incomparability.

I got around this by removing libvpd and lsvpd using synaptic. Then downloading those packages from debian (powerpc version not ppc64) and  installing using gdebi package installer. After this installing caja was no problem.

Hope this helps somebody!

---

