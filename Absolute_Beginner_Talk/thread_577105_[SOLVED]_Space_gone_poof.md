---
title: "[SOLVED] Space gone poof"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Niniel on 2007-10-15
It looks like the system updates are eating up free space in the worst way... could that be because of backups? If so, where are those stored so that I may delete them?

---

### Post by [S|G] on 2007-10-15
You can completely clear the apt cache using this command:
```
$ sudo apt-get clean all
```

---

### Post by Niniel on 2007-10-15
Fantastic, I did it and went from 4 MB to 780 MB free space. Neat.

---

