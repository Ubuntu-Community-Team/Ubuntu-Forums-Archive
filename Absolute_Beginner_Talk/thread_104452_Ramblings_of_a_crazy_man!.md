---
title: "Ramblings of a crazy man!"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by alamba on 2005-12-16
Hi everyone,

Had a general question regarding windoze & linux so not sure if i'm posting to the right forum. Some of the assumptions made would be due to a limited knowledge set. Just trying to find out which part of the thought process is wrong. Well, here goes...

1. Assumption 1: Windows XP pretty much runs on any platform right? I mean a x386 platform as against a AMD platform.

2. Assumption 2: From what I know, i've never seen a seperate XP edition for AMD platforms vs the regular x386 platform.

3. So why do we have seperate images for different platforms for ubuntu? I understand the concept of hardware stack and 64bit vs 32bit computing, etc. Just trying to figure is this true for windows (and i dont think it is) and if its not, why is it an issue for us?

4. Also, are the packages written also written for a specific architecture? That is, do i need to download a different package for say ntop for the different architectures?

Akshay

---

### Post by Knomefan on 2005-12-16
[http://www.microsoft.com/windowsxp/64bit/default.mspx](http://www.microsoft.com/windowsxp/64bit/default.mspx)

---

### Post by alamba on 2005-12-16
ahhh...thanks!! now i feel stupid.

btw...are the packages written also written for a specific architecture? That is, do i need to download a different package for say ntop for the different architectures?

---

### Post by Knomefan on 2005-12-16
Afaik yes. (Note, I never used amd64)
Btw., you can also happily use a "normal" ubuntu x86 on an amd64, but of course it won't take advantage of the 64bits then.

---

### Post by 23meg on 2005-12-16
There are lots of other architechtures than x86 and AMD64. Linux supports more than 20 architechtures (maybe even more?), whereas Windows is more or less x86 based, with a 64 bit variant.

Packages are *compiled,* not written, for different architechtures. There's usually one source, and many binaries compiled from it for different architechtures.

---

### Post by alamba on 2005-12-16
Cool. Thank you all.

Akshay

---

