---
title: "chmod +x and -x"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-05-21
How do I use 'chmod -x' to remove the execution permission to all **files** under a directory **and files in it's sub-directories**?

If I used the 'chmod -x' command, it affects my folders too, so I can't go in.  It's a real pain to add 'chmod +x' to all the folders one by one under a clustered folder.

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=tux101]How do I use 'chmod -x' to remove the execution permission to all **files** under a directory **and files in it's sub-directories**?

If I used the 'chmod -x' command, it affects my folders too, so I can't go in.  It's a real pain to add 'chmod +x' to all the folders one by one under a clustered folder.[/QUOTE]

I think you can use a -R flag to use chmod recursively. Alternitavely you can use --recursive flag.

---

### Post by mzilhao on 2006-05-21
i asked a similar question sometime ago. and i learned a cool trick. try:
```
find . -type f -exec chmod -x '{}' \;
```

---

