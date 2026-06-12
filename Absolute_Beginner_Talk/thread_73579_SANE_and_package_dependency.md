---
title: "SANE and package dependency"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by RandomGeek on 2005-10-09
Hello,

I'm trying to get a Canoscan LiDE 25 working with Breezy (RC).  Unfortunately I've hit a package dependency problem and would greatly appreciate some help!

There's a back-end called libsane and a front-end called xsane that depends on libsane.   However, my scanner is only supported by the latest nightly SANE so I have to install that from source rather than using packages.

I assumed that two sane backends shouldn't be installed together so I uninstalled the xsane and libsane that came with breezy and managed to install the latest SANE backend from source.  Now I want to install xsane to test the scanner but I can't do that in synaptic since it depends on the old libsane.

My question is: is there a way to install xsane using synaptic so that it uses the new SANE backend I installed manually?

Thanks a lot,
Chris

---

