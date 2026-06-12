---
title: "Just a bit of help with the terminal"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by grte on 2006-01-04
Okay, so what I want to do is create a list of all the files in a directory in alphabetical order.

I know to do this I would use the command ls -s > file_list.txt

However, say that I had my Audio directory.  Within that directory, I had many other directories for various artists, with the files inside those directories.

If I wanted to create a file list including all the files in all the directories for the different artists, what command would I use?

---

### Post by jpkotta on 2006-01-04
```
find ~/Audio -type f -exec basename '{}' \; | sort >file_list.txt
```

For more options:

```
man find
```
```
man sort
```

---

### Post by grte on 2006-01-04
Thank you

---

