---
title: "How do I untar lots of tarballs simultaneously?"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-11-16
I've mastered the *tar -xzvf Filename.tar.gz* command. Now, how do I apply that command to say, all the tarballs in a directory, rather than applying that command to them all individually?

---

### Post by aidanr on 2006-11-16
i assume it would be
tar -xzvf *.tar.gz

---

### Post by happy-and-lost on 2006-11-16
*! Duh!

When I do that, however, it presents me with lots of...

tar: filename.tar.gz: Not found in archive

?

---

### Post by sebbe1991 on 2006-11-16
```

for file in *.tar.gz; do tar zxvf $file; done;

```

---

