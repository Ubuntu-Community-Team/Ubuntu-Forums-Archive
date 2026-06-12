---
title: "rEFIt and warranty problems on macbook 5,1"
date: 2008-12-24
forum: Apple Hardware Users
---

### Post by hawkwing3141 on 2008-12-24
My Macbook 5,1 died unexpectedly the other day -- the LCD screen dissolved to white and would only show white on subsequent reboots, although i could hear MacOSX booting up in the background.  After resetting the SMC and NVRAM (as suggested on OSX forums) it stopped booting up at all.  I took it into the Mac store and they told me that rEFIt (v0.12) screwed up my EFI and they had to replace the logic board ($1000).  I don't know if this is true -- I rather suspect that it was something else and they took the opportunity to blame rEFIt because it is unsupported software that invalidates the warranty!  Thankfully the manager was merciful and fixed it under warranty, but I thought I would let people know that if they want their computer to be fixed under warranty they should remove rEFIt as soon as possible and just let Bootcamp load their Ubuntu OS so that the technicians can't blame warranty-covered problems on rEFIt.

---

### Post by mercenaryhmster on 2008-12-24
sadly, i think they were bullshitting you.  refit in no way violates the warranty of your apple, nor does it cause a white screen

---

### Post by Chrisj303 on 2008-12-25
I have sent my Mac in for repair, with rEFIt still installed a couple times - and they have never said anything.

I think you where being bullshitted,

---

### Post by cyberdork33 on 2008-12-28
Furthermore, since refit does not touch the EFI, that is a load of crap. If you want to remove it, start your mac in target disk mode, and connect it to another mac, remove the refit files, done.

[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

---

