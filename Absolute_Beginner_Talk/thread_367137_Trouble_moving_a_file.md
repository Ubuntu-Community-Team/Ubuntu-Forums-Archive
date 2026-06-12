---
title: "Trouble moving a file"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-02-21
I want to move a file from my Desktop to a folder in my FAT32 Windows partition, specifically to my My Documents folder.

Apparently the mv command has a problem when there is a space in the directory. I get an error message that says, "Documents/file" is not a directory. Is there any way around this?

---

### Post by lloyd_b on 2007-02-21
Enclose the arguments in quotation marks:

```
mv "this file.txt" "/windows/My Documents/this file.txt"
```

Lloyd B.

---

