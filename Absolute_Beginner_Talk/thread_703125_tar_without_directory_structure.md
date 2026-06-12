---
title: "tar without directory structure"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Deepak@CHN on 2008-02-21
Hi all,

I have a small issue with the tar command.

I am using 
```
tar -cvf /dir1/dir2/file.tar /dir1/dir2/A*.pdf
```

to tar all pdf files beginning with A in dir1/dir2.

I don't want the directory structure to be retained when i am extracting the files.

What options do i need to use when creating the tar file such that the directory structure is not retained.

Thx

---

### Post by freelinuxhelp on 2008-02-21
sorry, I was thinking cpio...

---

### Post by northern lights on 2008-02-21
Run the command from the parent folder of the pdfs:```

cd /dir1/dir2/
tar -cvf file.tar A*.pdf
```

[EDIT] - late - [/EDIT]

---

