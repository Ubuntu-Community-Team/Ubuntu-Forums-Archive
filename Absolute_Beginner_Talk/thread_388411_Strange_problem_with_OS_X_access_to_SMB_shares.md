---
title: "Strange problem with OS X access to SMB shares"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by OriginalGrumpyOldMan on 2007-03-19
OK, so I finally figured out how to set up samba users & password, and am finally able to access network shares (SMB) on my Ubuntu 6.10 install.

But here's the weird thing (on a Mac Mini):
--- Booting into Windows XP:
- Upload: OK
- Download: OK
--- Booting into OS X:
- Upload: OK
- Download: about a quarter of the normal speed ???

So, trying to get a file from the Ubuntu share will take approx. 10min. instead of ~2min. (!)
The _same_ file copied back to the _same_ Ubuntu share will finish in little over 2 min.

What's going? Any idea how to fix it?

Also, more generally, should I post this kind of questions in the Apple Intel Users forum? Or the Networking & security forum?

---

### Post by OriginalGrumpyOldMan on 2007-03-19
Got it to work. I don't know if I the first basic How-To I followed was too basic, or I made a mistake.

I restarted from scratch, using these instructions:
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

and this time everything works fine. It's just weird that it was only that one specific problem, and only in OS X...

---

