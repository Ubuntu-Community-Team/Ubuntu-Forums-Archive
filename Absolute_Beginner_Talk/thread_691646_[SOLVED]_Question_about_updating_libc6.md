---
title: "[SOLVED] Question about updating libc6"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by leileicats on 2008-02-08
Hi, folks. I need build the Intel Threading Build Block and I find the package will be attached with Ubuntu Hardy. 

And I am using Ubuntu Feisty 7.04. I am considering to download the .deb file and install manually. But the .deb files need dependices libc6_2.7-5ubuntu2, and my libc6 version is only  2.5-0ubuntu14. Is it safe for me to download the .deb file of libc6_2.7-5ubuntu2 and update manually? Or I need also update other components at the same time? Thanks.

---

### Post by yabbadabbadont on 2008-02-08
You are probably asking for trouble if you do that, since all the other packages on your system were built against an older version of the library.  If you want to try it anyway, make sure to create a full backup of your system first, so that it will be easy to recover if you run into major issues.

---

