---
title: "error edpkg Help!!!"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by shakeyfn on 2008-01-16
when trying to update i get this msg please respond " Edpkg interfence run 'Edpkg --configure -a' what is this and how do i correct this -thanks

---

### Post by Hospadar on 2008-01-16
Go to Applications->Accessories->Terminal and type "sudo dpkg --configure -a" (without the quotes)

The issue is you have some corrupted packages that are causing problems with dpkg, the package databases.  This command should fix these issues.

---

