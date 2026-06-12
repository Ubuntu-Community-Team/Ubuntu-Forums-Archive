---
title: "running OS selector with grub..!!"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by skopas on 2005-09-20
Yeah all, im running Acronis os selector, which is great has worked fine.  Though while installing ubuntu, it installed grub to the mbr.....now im wondering if im going to have problems with os selector.  ;-) 

RIght now im running off of grub.  Kinda afraid to configure back to os selector in thinking it's will mess things up.  not sure though.

any thoughts on this , would be greatly appreciated.

---

### Post by SilentCacophony on 2005-09-20
Hello. I had a similar situation when I installed Ubuntu. I had used Ranish Partition Manager's boot selector prior to installing Ubuntu, and also let grub overwrite the mbr. When I attempted to restore the boot selector to Ranish, I couldn't figure out how to configure it to boot linux partitions (the documentation is scarce,) so it only booted my windows partition. After that, I decided to restore grub.

Anyhow, my humble advice would be to leave grub there, and read up on it a bit. The online docs are [here](http://www.gnu.org/software/grub/grub-legacy-support.en.html). It's really quite configurable and powerful, once you know how it works.

---

