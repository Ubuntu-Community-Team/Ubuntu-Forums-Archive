---
title: "Bad installation of rEFIt"
date: 2009-11-07
forum: Apple Hardware Users
---

### Post by rockstar1 on 2009-11-07
Hi, Finally I install ubuntu 9.10, in my MacBook 5,1, so I want to have double boot with Snow Leopard and Ubuntu. I try to install rEFIt, I downloaded .dmg to run rEFIt.mpkg, and choose the partition where I installed Leopard. 
I did the same operation for three times and then I restarted my MacBook, but rEFIt can't install on my Mac. Anybody can help me?

---

### Post by DCM36 on 2009-11-08
Try running this command in an OS X Terminal window (Applications>Utilities>Terminal)

```
sudo /efi/refit/enable-always.sh
```

The rEFIt menu should appear on the next boot

---

### Post by rockstar1 on 2009-11-08
Yes, you right, Finally I could install rEFIt.
Thanks!!

---

