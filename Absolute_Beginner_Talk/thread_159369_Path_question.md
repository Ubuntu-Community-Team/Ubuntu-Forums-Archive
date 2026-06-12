---
title: "Path question"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by georgepds on 2006-04-12
Rank beginner here. I'm trying to compile and run a program that needs plotmtx which resides in usr\X11R6\bin. I know I can do the following in each terminal window

PATH=usr\X11R6\bin:"${PATH}"

but I wonder where it belongs. I looked in my home directory, and there is no .login

Shoud t go in the .bash_prof (there are other path statements there)

---

### Post by taurus on 2006-04-12
It should belong in ~/.bashrc and it is /, not \...
```

PATH=$PATH:/path/to/new/directory
export PATH

```

---

