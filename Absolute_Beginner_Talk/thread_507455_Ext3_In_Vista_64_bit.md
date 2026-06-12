---
title: "Ext3 In Vista 64 bit?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ocho on 2007-07-23
I was wondering if there is anyway to mount an Ext3 partition in 64 bit Vista. I have found ways to do it in 32 bit Vista, none of which work with my x64 Vista Ultimate. Any ideas?

---

### Post by xubu_caapn on 2007-07-23
huh? do you want to mount an ext3 partition in vista or 64 bit ubuntu? for ubuntu, there'd be no problem, but your question confuses me...

---

### Post by ocho on 2007-07-23
Whoops. I didn't read over my original message, it's completely contradictory! Sorry about that.

What I'm trying to do is mount an Ext3 partition--my Ubuntu partition-- in 64 bit Vista.

---

### Post by doublemeat on 2008-03-30
[http://www.fs-driver.org/](http://www.fs-driver.org/)


Better late answer than never.  Actually I think they just recently added 64-bit Vista support.  It mounts ext2 volumes, or ext3 volumes as ext2--which works just fine and doesn't mess up Ubuntu.  It just doesn't support journaling which ext3 normally does when Linux is running.

---

