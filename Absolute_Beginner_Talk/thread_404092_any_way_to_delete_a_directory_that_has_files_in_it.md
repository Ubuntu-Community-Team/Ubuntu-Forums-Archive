---
title: "any way to delete a directory that has files in it?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Mike1971 on 2007-04-07
Hi,

Wondering if there is a way to delete a directory that has files in it. I don't want to go through the process to delete every file in the directory one by one.

Thanks

---

### Post by mac.ryan on 2007-04-07
```
rm -dr NameOfYourDirectory
```

type "man rm" to see how it works ;)

---

### Post by Jovec on 2007-04-07
Assuming you have the proper permissions to delete the directory and files inside, you can do this from a terminal with:

```
rm -rf <dirname>
```

Of course, you could also use a GUI file manager like Nautilus to do this.  If you do use the command line, you won't be able to restore the files easily, as it does not move them to the Trash folder.

---

### Post by bashologist on 2007-04-08
I agree with the above comment. To move a folder to the trash you could do this:
```
mv <dirname> ~/.Trash/
```

---

