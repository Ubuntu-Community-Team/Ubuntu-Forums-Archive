---
title: "samba input/output error"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by rshel on 2007-09-05
Hi

I have a NAS that I mount permanently in fstab; it works fine except when I try to move or copy fairly large (1 gig) XXX.tgz files from my home directory to a directory on the samba share.  Then I get a message that the files cannot be moved because of an input/output error.   I've seen discussion of similar problems elsewhere but no solutions.  I have no problem moving individual, large, non-tarred files.  This occurs whether I initiate the move through a script or through nautilus.  Any ideas why this would happen?

Thanks

---

### Post by rshel on 2007-09-05
bump

Ah-ha.  My tar files had a $STAMP added to them, which seemed to cause the problem.  When I removed it, all went well.

---

