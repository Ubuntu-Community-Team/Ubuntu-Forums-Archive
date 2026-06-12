---
title: "i was just wondering if this is possible"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Kedster on 2008-03-13
ok if i install my home on a different hard drive  could i take out that hard drive and put it in a different computer with abuntu will i be able to logn with my home stuff 
as in using it not just seeig it

---

### Post by PeterJS on 2008-03-13
if you have a user account on the second machine with the exact same name and userID. Passwords, userID, groups, etc are stored in:
/etc/passwd
/etc/shadow
/etc/group
/etc/gshadow

So I'm going to guess no.

---

### Post by PurposeOfReason on 2008-03-13
If you move your hdd from one computer to another and the computer you move it too has no hdd in it until you put the moved one in, possibly. Hardware might cause an issue though. Might as in will unless they're the same.

---

