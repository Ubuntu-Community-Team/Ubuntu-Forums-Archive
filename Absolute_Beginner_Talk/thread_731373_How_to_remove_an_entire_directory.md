---
title: "How to remove an entire directory"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-03-21
What is the command to remove an entire directory?

i tried "sudo rm (path)"  but that tells me that: *** is a directory

---

### Post by Barrucadu on 2008-03-21
To remove an entire directory and all contents within, disregarding any warnings (assuming you have write permissions to it, of course...)

```
rm -rf directory
```

---

