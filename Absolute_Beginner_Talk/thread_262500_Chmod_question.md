---
title: "Chmod question??"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Styles on 2006-09-21
Looked on the chmod man page and tried to Google for my answer and found nothing, so here is my quandry maybe you can help?

Can a member of a group use chmod to change permissions on a file which belongs to the same group, or can only the owner of the file use the chmod command?

My testing shows only the owner can chmod the file and not group members, I'm I right or wrong? Your thoughts???

Cheers,
Styles

---

### Post by Virak on 2006-09-21
Quoth the chmod(2) manpage:
> The effective UID of the calling process must match the owner of the file, or the process must be privilegedSo I'd say you're right.

---

### Post by Cruz on 2006-09-21
Tried it, got the same result.

---

