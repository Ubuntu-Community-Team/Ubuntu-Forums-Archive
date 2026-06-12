---
title: "INC backups ???"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by lost4now on 2008-02-26
Would someone please clear up this question for me.

Example:

last week I did a full backup. 
Yesterday I did an incremental backup
Today I did another inc backup

The system crashes

I restored the full backup
to bring the system up to where it was this morning do I have to restore both INC backups or will the one marked today do it for me.

Thanks

---

### Post by mulino on 2008-02-26
Hello!

Incremental backups only hold the changes between the backups you did so far. It doesn't matter, if the last backup was a full backup or only an incremental one: it saves only the changes.

So you have to restore the full backup first, then restore all incremental backups one by one in the correct order.
Hth, /mulino

---

### Post by lost4now on 2008-02-26
Thanks thats exactly what I needed to know

---

