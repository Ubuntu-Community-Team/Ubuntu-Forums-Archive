---
title: "Extracting .tar.bz2 file via Console"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-02-20
The title pretty much says it all. I just need to know the command(s) so I can throw [FONT="Courier New"]sudo[/FONT] in front of it.

---

### Post by yabbadabbadont on 2007-02-20
tar xvjf tararchivefilename.tar.bz2

Edit: man tar for details of the options used.

---

### Post by Zuuswa on 2007-02-20
```
tar
```
but you might want to do a 'man tar' or 'tar --help' for some helpful arguements to pass to the application

---

### Post by 42Wired on 2007-02-20
How can I make a new folder to put the contents in?

---

### Post by Maestro23 on 2007-02-20
> **42Wired said:**
> How can I make a new folder to put the contents in?

mkdir foldername

---

### Post by Bachstelze on 2007-02-20
If the tarball has been properly made, it should automagically create one when you extract it.

---

### Post by 42Wired on 2007-02-20
> **HymnToLife said:**
> If the tarball has been properly made, it should automagically create one when you extract it.

I'm getting the same message even though the destination directory exists now.

What do you mean by tarball?

---

### Post by Bachstelze on 2007-02-20
A "Tarball" usually refers to a .tar.* archive. What message are you getting ?

---

### Post by Tomosaur on 2007-02-20
To extract tar.bz2 files:
```

tar -xvf my_file.tar.bz2

```

This will also create a folder for the extracted files to go into.

---

### Post by 42Wired on 2007-02-20
tar: [directory] not found in archive
tar: Error exit delayed from previous errors

---

### Post by Bachstelze on 2007-02-20
just do

```
tar xjvf filename.tar.bz2
```

---

### Post by 42Wired on 2007-02-20
Putting that in just prints a list of files.

---

### Post by Bachstelze on 2007-02-20
Yes, it's normal, tar shows you the name of the files as they are extraced - drop the v from the command if you don't want that. Anyway, now you should have a dir - typically with the same name as the archive - where it was extracted.

---

### Post by 42Wired on 2007-02-20
Now how do I make it extract to a specific directory?

---

### Post by Bachstelze on 2007-02-20
tar xjvf filename.tar.bz2 -C /path/to/dir/you/want/to/extract/to

---

### Post by 42Wired on 2007-02-20
Perfect now. Thanks.

EDIT: One more thing, then I promise I'll leave you alone. How do I rename a directory?

---

### Post by yabbadabbadont on 2007-02-21
> **42Wired said:**
> Perfect now. Thanks.

EDIT: One more thing, then I promise I'll leave you alone. How do I rename a directory?

mv OldDirectoryName NewDirectoryName

---

