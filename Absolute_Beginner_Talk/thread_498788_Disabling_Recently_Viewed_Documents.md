---
title: "Disabling Recently Viewed Documents?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-07-11
Hi, i was just wondering if there was a way to disable recently viewed documents in the main menu. Thanks

---

### Post by 5-HT on 2007-07-11
Clear the recently used list, and then make the file read-only:
chmod 400 ~/.recently-used

cheers,

---

### Post by Vajra Vrtti on 2007-07-12
I have a list of recently used documents under the Places menu but a have no ~/.recently-used folder.

---

### Post by 5-HT on 2007-07-12
There's been a change somewhere along the line...
This should do it:[code]
rm ~/.recently-used ~/.recently-used.xbel && mkdir ~/.recently-used.xbel

---

