---
title: "using apt, but then manually upgrading specific applications"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-12-14
Hi,

If I use apt to install an application and then latter upgrade that application, will apt then downgrade the upgraded app??

Thanks

---

### Post by lance_klusener on 2006-12-14
No i dont think so.

---

### Post by muep on 2006-12-14
If you install a *.deb file with a newer package, apt will probably accept the new version just fine. On the other hand, you can also manually install the new version somewhere else, in your home directory for example. Then apt will manage the default as it used to and you can use the new version.

---

