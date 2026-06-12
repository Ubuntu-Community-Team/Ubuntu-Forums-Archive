---
title: "Openoffice hangs with JRE enabled SOLVED"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by rajeev1204 on 2006-12-09
hi

i managed to solve this problem by selecting the 32 bit sun java version from the repos.

also most importantly , i typed in terminal :

" sudo update-alternatives --config java".

This lists all the available java versions .select 32 bit SUN VERSION .

then in office in tools/options/java select this version.

Problem solved

---

