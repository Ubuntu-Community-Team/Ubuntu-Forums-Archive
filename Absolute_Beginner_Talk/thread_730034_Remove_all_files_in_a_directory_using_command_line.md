---
title: "Remove all files in a directory using command line"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by phillip_peters52 on 2008-03-20
Does anyone know a command which will allow to remove all the files in a directory at once as 

rm [filename] only removes a single file
and
rmdir [directory name] only removes an empty directory

---

### Post by PeterJS on 2008-03-20
There isn't a command to delete all the files in a directory persay. But what you can do is use shell wild cards to generate a list of all the file names in a given directory and then have rm delete that:
```

rm ./*

```

---

### Post by munkyeetr on 2008-03-20
**** BE VERY CAREFUL YOU DO NOT RUN THIS ON YOUR ROOT DIRECTORY !!!! 

This will remove files and directories (empty or not)

```

rm -r /path/to/folder/*

```

If you just need files use:
```

rm /path/to/folder/*

```

---

### Post by jordanmthomas on 2008-03-20
What others have suggested removes only the files inside a directory (like you asked)
If you just want to remove the whole directory at once (so you don't have to use rmdir)
```
rm -r directory
```

---

### Post by phillip_peters52 on 2008-03-20
Thanks everyone that worked fine using 

#sudo rm -r [directory]

---

### Post by StOoZ on 2008-03-20
to remove all files inside a directory you can also use:
> rm *
when you inside that particular dir.

---

### Post by stchman on 2008-03-20
> **phillip_peters52 said:**
> Does anyone know a command which will allow to remove all the files in a directory at once as 

rm [filename] only removes a single file
and
rmdir [directory name] only removes an empty directory

I use the rm command.  It is a power yet dangerous command.  If you misuse the rm command it is highly unlikely that you will get your files back EVER.

```
rm -r -f <directory you want to remove>
```

rm - remove
-r  - recursive (will include sub-directories)
-f  - force no matter what the permissions

Put a sudo in front for root privileges.

The rmdir command will not remove directories if they are populated.

---

### Post by photonian on 2008-03-20
rm -r -f directory

This is a very dangerous command
Be Careful

---

