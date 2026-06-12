---
title: "Cannot manipulate on mounted partition, why ?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by mocqueanh on 2007-05-27
I mounted my Windows partition, and want to delete some file, folder in Ubuntu.
But after mounted, i only can manipulate (delete, copy, and other commands ) on files and folders in level 1.
For example: my Win partition has some folders and files: 
-Folder 1
-Folder 2
-Folder x .......
-File 1
-File 2
-File x ..........

I can delete, copy, etc.... on these file, folder.

But when i want to manipulate on file, folder inside Folder 1, Folder 2,......., i cannot.

Example: when i type command:

ls -lh /mnt/win1/Folder1/Folder2

I always receive error message: No such file or directory.
I cant understand ?

---

### Post by darklemming54 on 2007-05-28
The problem might be that the command line doesn't allow you to copy, move, etc files that have spaces in the name or are in folders with spaces in the name.  Try opening Nautilus as root with 

```

gksudo nautilus

```

then do what you want with the files

---

### Post by mocqueanh on 2007-05-29
Thank for answer, but i found the cause.
This is my misstake, i type wrongly the name of file

The file name is: Ubuntu_ guides
But i just type: Ubuntu_guide

( miss a space character)

Sorry very much.

And by the way. if you want to manipulate on file, folder that contain space character in the Terminal, you put the name of file, folder in a " "

For instance:

```
sudo rm /home/cuong/"my test folder"
```

---

