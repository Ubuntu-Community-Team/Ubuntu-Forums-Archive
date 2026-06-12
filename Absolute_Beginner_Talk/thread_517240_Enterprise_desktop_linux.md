---
title: "Enterprise desktop linux"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-08-04
(just out of curiousity) Can I use an enterprise linux desktop as a regular desktop os? are there any pros or cons? e.g., cent os?

---

### Post by Brunellus on 2007-08-04
I don't understand the question.

The only difference between "enterprise"/ "commercial"  distributions and "community" distributions is usually the support contract.  The underlying software is largely the same.

In fact, "enterprise" versions may have somewhat older/more stable software, while "community" versions tend to be a bit closer to the bleeding edge.  A single home user might be OK with the odd breakage--but new bugs and breakges will really kill the enterprise user.  This is why many servers run Debian Stable in preference to Debian Unstable or Ubuntu.

---

### Post by arijarot on 2007-08-04
So, the only real difference is one is commercial (enterprise = commercial) and one is community based? say, e.g., suse linux enterprise desktop vs opensuse --same logic?

---

### Post by Brunellus on 2007-08-04
> **arijarot said:**
> So, the only real difference is one is commercial (enterprise = commercial) and one is community based? say, e.g., suse linux enterprise desktop vs opensuse --same logic?
more or less.  I haven't run SuSE since they were at version 9.1, so I can't tell you about the OpenSUSE/SLED governance structure at all.  

In general, however, commercial distributions aim for stability over new features;  the cost associated in acquiring them is the cost of a service contract with the software vendor.  CentOS (which is repackaged .srpms of RHEL), for instance, can be freely downloaded/built, but the developers offer support for it as a paid option.   Alternatively, you could purchase a support contract with Red Hat which gets you RHEL.  Or you could run Fedora Core.  

None of this is terribly relevant to individual home/hobbyist users, but for corporate sysadmins, the support contract is a good insurance policy, especially when pitching the software acquisition to VERY non-technical superiors.

---

### Post by arijarot on 2007-08-04
Great! that clarifies things, thanks.

---

### Post by Brunellus on 2007-08-04
> **arijarot said:**
> Great! that clarifies things, thanks.
wasn't always the case though.  SuSE used to be a part-Free distribution.  Their excellent install/setup utilities--YaST, YaST2, SaX and SaX2--used to be proprietary.

---

