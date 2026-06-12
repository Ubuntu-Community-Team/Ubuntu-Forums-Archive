---
title: "&quot;Error while Moving&quot; when trying to move shared file"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by usersock on 2007-11-12
**I'm not able to remove files from my Ubuntu shared folder (in Ubuntu)**. I can move things to and from my XP shared folder while in Ubuntu, and on my XP computer everything works just fine (can do everything with the Ubuntu shared folder). 

I receive the following error: 
Error while Moving.
*"/home/shared/image.png"* cannot be moved because you do not have permissions to change it or its parent folder.

---

### Post by geirha on 2007-11-12
what are the permissions? The output of these commands will help 
```
ls -ld /home/shared /home/shared/image.png
groups

```

---

