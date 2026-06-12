---
title: "what are... symbolic links?"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by pigmelt on 2005-10-22
what are symbolic links and what to they do?

---

### Post by aysiu on 2005-10-22
As far as I can tell--and people can tell me if I'm wrong--they're the equivalent of shortcuts (Windows) or aliases (Mac).

---

### Post by DJ_Max on 2005-10-22
[QUOTE=aysiu]As far as I can tell--and people can tell me if I'm wrong--they're the equivalent of shortcuts (Windows) or aliases (Mac).[/QUOTE]
That's a good comparison.

For more info, via the command line.
```
info coreutils ln
```

[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

---

### Post by pigmelt on 2005-10-22
[QUOTE=aysiu]As far as I can tell--and people can tell me if I'm wrong--they're the equivalent of shortcuts (Windows) or aliases (Mac).[/QUOTE]
thanks just trying to learn, just install realplayer using some help in the forum, i've been trying to install it for a few days now, and got it to the set up mode,then it asked for a symbolic link. so thanks for the answer. all the info is great. this is the first time i have actualy got any thing installed on my pc that did not give me trouble getting it done.thanks

---

### Post by blastus on 2005-10-22
Every file has an inode number associated with it. Every file also has at least one pointer associated with it. For example, if you create a file called "test", the file will have an inode number and one pointer associated with it. A hard link is a pointer to a file, and a symbolic link is an indirect pointer to a file.

Symbolic links are like shortcuts in Windows but they are more powerful. For example, you can have a symbolic link to a directory. In Linux, you can also use a symbolic link to a directory or a file as though the link was the actual directory or file. Deleting a symbolic link does not delete the directory or file the link points to. Like in Windows, if you delete the directory or file, the symbolic links to it still exist but are broken. In Windows, shortcuts are pretty much only useful for putting an icon on your desktop or quick launch. In Linux, symbolic links are much more useful because they can point to directories and because you can use the link as though you where using the actual directory or file.

There is no equivalent to a hard link in Windows. When you create a hard link to a file, you create an additional pointer to that file. The difference between hard links and symbolic links is that all hard links are treated equally. If you have a file called "test1" and create a hard link to it called "test2", the actual file now has two pointers associated with it. If you delete the "test1" file, you can still access the file through "test2." When the last pointer to the file is deleted, the system deletes the file.

One difference between hard and symbolic links is that you cannot create a hard link to a directory, but you can create a symbolic link to it. Another difference is that permissions are not applicable to symbolic links, but with hard links, because there is only one file, the file status information (which includes permissions) is the same for all links.

---

### Post by idn on 2005-10-22
Thanks that was very interesting, I didnt know that before

---

