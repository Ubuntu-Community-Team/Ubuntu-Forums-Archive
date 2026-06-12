---
title: "How do you find folders"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by DaddyUnit on 2008-03-11
I found "search for files" but it doesn't seem to work on folder names. I've installed CVS so I know there must be a CVSROOT folder somewhere on the machine, but I can't find it. Is there any way to search for folders?

---

### Post by drdrewdown on 2008-03-11
in terminal you can type : whereis ****

as in whereis java

---

### Post by spydon on 2008-03-11
Search for files should work on folders too...

If you want to do ```
whereis fileorfoldername
``` as drdrewdown said then do  ```
updatedb
``` first so it updates the database with new folders and files.

---

### Post by Arkenzor on 2008-03-11
You can use the **find** command-line utility. It has a huge number of options (which I strongly suggest taking a look at, that's one really useful program), but you can get by with what you're trying to do by simply typing this:
```
find some-base-folder -iname cvsroot -type d -print
```

- some-base-folder will be the base of the directory tree searched, e.g. "/" if you're really desperate. 

- -iname cvsroot means we're looking for files called "cvsroot". The "i" in "iname" stands for case-insensitive.

- -type d means we're only interested in directories.

- -print specifies what we want to do with these files: print their full location.


If you think there's a possibility that the folder you're looking for is in an area where your user doesn't even have read access, then you'll need to run the command with sudo.


EDIT: Seems I take a bit too long writing my replies these days...
Also, I've just read the man page for whereis and I don't think that's what it's supposed to do.

---

### Post by bodhi.zazen on 2008-03-11
You can also use find

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

find is quite powerful and can do much more :)

---

### Post by DaddyUnit on 2008-03-11
Thanks everyone. I'm wondering if it indeed is somewhere I don't have access (although I installed it??). So far nothing's turning up, so I wonder if I'm either looking for the wrong thing or for something that doesn't exist. the search continues. What is "sudo" by the way?

---

### Post by Arkenzor on 2008-03-11
Prefixing a command with "sudo", like in the case I was talking about
```
sudo find / -iname cvsroot -type d -print
```
means it will be run with full administrator rights. That's not something to use without thinking first, but it's often necessary for maintenance (since unlike Windows, in the Linux security model normal users only have very limited rights. They can basically only modify the files they created themselves).

This said, the huge majority of your "system files" will be at least accessible for reading. If the standard permissions don't even allow you to read a file it probably means you'd best not tamper with it.

---

