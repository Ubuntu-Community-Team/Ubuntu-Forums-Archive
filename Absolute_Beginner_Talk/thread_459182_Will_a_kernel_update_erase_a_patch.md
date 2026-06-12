---
title: "Will a kernel update erase a patch?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by clcaus on 2007-05-30
Quick question: I had to patch my kernel to get suspend working on an Intel MacBook. Ubuntu is now telling me that I need a kernel update for security reasons. If I do the automatic update, will I lose the patch I applied?

---

### Post by Cypher on 2007-05-30
If it was a source-level patch that you applied, then built a Kernel and have been using, then yes allowing Ubuntu to do the Kernel update will not take your patch into affect. This is because you're essentially getting an entirely new Kernel to boot.

You might want to check out the changelog for new Kernel that wants to be installed and see if your issue is fixed there..

---

