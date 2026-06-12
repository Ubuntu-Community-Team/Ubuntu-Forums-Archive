---
title: "rename files in standart input"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-12-30
Is there command that renames all the files that are in the standart input?

---

### Post by rich.bradshaw on 2007-12-30
You can just use mv to rename files, as in

mv oldname newname

You could use a loop to feed the output from ls into this to rename them.

What do you want to do exactly?

---

### Post by Fixman on 2007-12-30
> **rich.bradshaw said:**
> You can just use mv to rename files, as in

mv oldname newname

You could use a loop to feed the output from ls into this to rename them.

What do you want to do exactly?

Well, I actually mean to use some kind of mv that, instead of getting the filenames from the arguments, gets them from the standard input.

---

### Post by rich.bradshaw on 2007-12-30
As in, you want to pipe something into mv?

something like cat files.txt | some-mv-command

That would rename the filenames in files.txt?

---

### Post by Fixman on 2007-12-30
> **rich.bradshaw said:**
> As in, you want to pipe something into mv?

something like cat files.txt | some-mv-command

That would rename the filenames in files.txt?

That same.

---

### Post by nick_h on 2007-12-30
Use the xargs command.

For the manual page, type:
```
man xargs
```

Example:
```
ls xxx* | xargs /usr/bin/rename 's/xxx/yyy/g'
```
changes xxx to yyy in files provided by stdin.
(obviously the command as it stands could be done without xargs)

---

