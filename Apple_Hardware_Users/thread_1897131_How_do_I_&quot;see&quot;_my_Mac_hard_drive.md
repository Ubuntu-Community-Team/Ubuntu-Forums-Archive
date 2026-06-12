---
title: "How do I &quot;see&quot; my Mac hard drive?"
date: 2011-12-18
forum: Apple Hardware Users
---

### Post by PoliticsReSpun on 2011-12-18
How do I "see" my Mac hard drive while I've booted in Ubuntu? I have a dual boot and I can't "find" it.

Muchos nachos!

---

### Post by Lars Noodén on 2011-12-18
You need to have the package 'hfsplus' installed.  It probably does not hurt to also have 'hfsutils' and 'hfsprogs' installed, too.

---

### Post by PoliticsReSpun on 2011-12-20
> **careyjesus said:**
> you can contact to your administrator.

thanks.  :)

it's my own computer. i am the administrator. :)

---

### Post by PoliticsReSpun on 2011-12-21
> **careyjesus said:**
> oh.so have you done shortout of your problem?

still working through the hfsplus, etc. suggestions above. not quite figure out write access just yet.

---

### Post by Lars Noodén on 2011-12-21
> **PoliticsReSpun said:**
> still working through the hfsplus, etc. suggestions above. not quite figure out write access just yet.

If I understand correctly, for write access in Linux, you have to have journalling in HFS+ turned off.

---

