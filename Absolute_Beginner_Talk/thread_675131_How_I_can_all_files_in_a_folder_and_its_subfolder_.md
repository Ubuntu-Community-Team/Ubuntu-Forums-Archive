---
title: "How I can all files in a folder and its subfolder which has legolas inside thier text"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-22
Hi
Thank you for reading my post
I want to find all text files that has legolas word inside their text.
files are located in a folder and tens of its sub folders.
Files extension is txt.
I find that there is a command named "find" which can find a file with an specific name but i do not know now to make it search inside all text files in a folder and its subfolders.


Thanks

---

### Post by stump138 on 2008-01-22
```
locate *.txt | grep legolas
```

---

### Post by PeterJS on 2008-01-22
try:
```

grep legolas -R folder

```

---

