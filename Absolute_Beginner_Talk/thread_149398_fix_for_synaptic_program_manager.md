---
title: "fix for synaptic program manager?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by cellarguy on 2006-03-23
I had a big crash today, and it took me several hours of glancing through these forums for info on how to fix it while using only my live cd.  But the info was there, thanks all.

I'm up and running again, but there are problems.  Had to run **fsck** before Linux would boot, and several inodes were corrupt.

The crash occurred when I was using **Synaptic Program Manager**, and it failed to write the dpkg because the entire *OS* went read-only.  Now I can't use **synaptic pkg man** at all.  


```
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: Unable to lock the list directory
```

Any suggestions for reinstalling the list of repositories?

---

