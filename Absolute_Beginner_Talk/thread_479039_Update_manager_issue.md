---
title: "Update manager issue"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by sixou on 2007-06-19
Hi,
I have a problem with the update manager, i get an error that says...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.


when i hit the close button snyaptic shuts down. it worked for a while but now nothing


After running the script in the terminal I had the following result:

dpkg: parse error, in file `/var/lib/dpkg/updates/0015' near line 1:
newline in field name `#padding'

I tried to edit the file but the file was empty. I also tried to run the update manager again, but the same errors comes up. What should I do?

---

### Post by yabbadabbadont on 2007-06-19
Edit: Never mind.  I reread your post and realized that you had tried what I suggested.

---

### Post by sixou on 2007-06-20
Ok I found the answer here :
[http://lists.debian.org/debian-dpkg/1998/06/msg00130.html](http://lists.debian.org/debian-dpkg/1998/06/msg00130.html)

I had to delete two files before running the script in terminal which repaired my system. 0015 and 0016. I knew that because after removing 0015, running the script would tell me that there was an error in 0016.
Then the script repaired update manager which is running without fault now.

---

