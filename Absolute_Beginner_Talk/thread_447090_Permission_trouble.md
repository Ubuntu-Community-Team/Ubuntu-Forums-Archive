---
title: "Permission trouble"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by HenningS on 2007-05-17
So I have this external harddrive formatted in HFS (I think), which i connected to my Ubuntu comp. I couldnt do anything, because i was not the owner. I went back into OS X, changed the permissions to 'anyone', went back into Ubuntu. Everything was fine, until I wanted to copy a picture into one of the folders in Banshee's library. Now my question is: How do I 'get' the permissions to do **anything** I want on that harddrive?

---

### Post by Quintin Riis on 2007-05-17
I don't believe that HFS+ has write support in Ubuntu at this time.  You'll need to use FAT32 or maybe UFS, or look at a solution like [http://sf.net/projects/linux-hfsplus](http://sf.net/projects/linux-hfsplus)

---

### Post by HenningS on 2007-05-17
Sounds plausible. Not good, but plausible. Thanks for helping anyway.

---

