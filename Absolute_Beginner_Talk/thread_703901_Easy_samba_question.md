---
title: "Easy samba question"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Jloser on 2008-02-21
So I got my network all setup and I am able to access files from each PC to every other PC, Now I have a question about how my ubuntu laptop "sees" my windows files.

Problem is when I browse to any windows machine (XP or Vista) from my ubuntu laptop it shows the share folder just fine, but then it also displays all valid drive letters with a $ after them.  These aren't shared on the windows PCs, so why are they visible to the linux pc?  I can't see the contents of the drives, but all the drives displayed are valid.  Also from windows to windows this information is not displayed.

Thanks in advance!

---

### Post by HermanAB on 2008-02-21
[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by Austin_KW on 2008-02-21
Administrative shares on non simple file sharing
i.e these are default shares available to any admin user. \\ComputerName\(Drive letter)$

---

