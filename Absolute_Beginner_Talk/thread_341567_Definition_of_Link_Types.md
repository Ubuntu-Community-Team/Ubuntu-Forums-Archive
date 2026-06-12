---
title: "Definition of Link Types"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-01-18
I've read my "Linux in Easy Steps" book and have a question that I didn't get the answer to.  What is the difference between a "Hard Link", "Soft Link", and "Sym Link"?

---

### Post by 23meg on 2007-01-18
Think of hard links as just a method to create a new file name for the same content on the disk. When you create a hard link called "file_b" for a file called "file_a", the two filenames point to the same *inode* (the basic filesystem data structure) on the disk, have the same size, same attributes, so on. Even if you delete your original "file_a", the same content is still available under "file_b" which you created with the hard link command. Hard links cannot point outside the filesystem and cannot be used with directories. To create a hard link, use the "ln" command.

Symbolic link, soft link and symlink refer to the same thing; it just contains a pointer (path name) to a target file. When you delete the original file, the symlink becomes useless. Symlinks can cross filesystem borders and you can use them with directories as well. To create a symlink, use "ln -s".

---

