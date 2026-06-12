---
title: "Problem with terminal and spaces [Resolved]"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Southbound on 2007-05-17
Whenever I run into a file or directory that contains a space I don't know how to handle it in the terminal.

If I have two files: "nospaces.file" and "one space.file",

"rm nospaces.file" works fine, but "rm one space.file" gives me 
 
rm: cannot remove `one': No such file or directory
rm: cannot remove `space.file': No such file or directory

What do I do here?

---

### Post by aysiu on 2007-05-17
```
rm one\ space.file
```

---

### Post by Southbound on 2007-05-17
Thanks!

---

