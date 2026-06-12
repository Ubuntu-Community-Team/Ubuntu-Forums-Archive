---
title: "lame segfaults on ppc?"
date: 2005-09-09
forum: Apple PPC Users
---

### Post by jstultz on 2005-09-09
Running Hoary (everything current as of today) on my mac mini:
I've recently noticed lame (3.96.1-1) is segfaulting and occasionally dumping lots of: "ResvSizeInternal buffer inconsistency. flushbits <>" errors. 

Google suggests this could be a bad-memory issue (which would be a pain as I did upgrade the memory 2-3 weeks ago), however I have not noticed any other instabilities. Building kernels works fine. I ran memtest overnight w/o issue. 

Are there any other ideas for helping narrow this issue down?

---

### Post by jstultz on 2005-09-11
Hmmm. On bit of interest I left out: I was running with a 2.6.13-rc6-ish kernel. Rebooting with a new 2.6.13-git kernel seems to have resolved the issue, but I'm watching it closely.

---

