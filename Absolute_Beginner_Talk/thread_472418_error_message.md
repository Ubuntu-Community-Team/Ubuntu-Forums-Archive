---
title: "error message"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Colin Lenton on 2007-06-13
When trying to install updates i get the following error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

What does this mean and what do I have to do?

Thanks

---

### Post by 5-HT on 2007-06-13
There may have been an issue opening the cache during installation. 
Did you try running ```
sudo dpkg --configure -a
``` as suggested by the error message?

---

