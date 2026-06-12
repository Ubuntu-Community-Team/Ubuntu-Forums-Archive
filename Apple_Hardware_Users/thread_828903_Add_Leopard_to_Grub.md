---
title: "Add Leopard to Grub"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by ankitguptag18 on 2008-06-14
hi,

I had Leopard installed on my Laptop for past 3 months, 
suddenly my Leopard partion (hd0,4) is missing from the grub 
can any ony say me what to do

I tried 

title		Leopard
root		(hd0,4)
savedefault
makeactive
chainloader	+1
quiet

but it didnot work.

I am Using UBUNTU 7.10

---

### Post by cyberdork33 on 2008-06-14
you shouldn't be loading Leopard from GRUB. The Mac can load it from EFI.

---

