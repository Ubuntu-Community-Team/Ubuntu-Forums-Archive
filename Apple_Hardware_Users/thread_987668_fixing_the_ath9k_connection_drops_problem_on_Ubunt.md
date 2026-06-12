---
title: "fixing the ath9k connection drops problem on Ubuntu8.10"
date: 2008-11-19
forum: Apple Hardware Users
---

### Post by xiaoqiangwj on 2008-11-19
Hey guys, I'm following the instruction from
 [http://bugzilla.kernel.org/show_bug.cgi?id=11394](http://bugzilla.kernel.org/show_bug.cgi?id=11394)
to fix the ath9k connection drops problem on Ubuntu8.10.
I download the wireless-3.6 file, and I dont know how to apply to the patch file.

I tried 
patch -p0 <ath9k-seqno.patch
and I got this:

can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/net/wireless/ath9k/beacon.c b/drivers/net/wireless/ath9k/beacon.c
|index caf5694..00a0eaa 100644
|--- a/drivers/net/wireless/ath9k/beacon.c
|+++ b/drivers/net/wireless/ath9k/beacon.c
--------------------------
File to patch: 

so where's the file I need to apply to the patch?
I think it's the file "wireless-3.6", but I use git, and I got a folder.

Really no idea.
Thanks!

---

