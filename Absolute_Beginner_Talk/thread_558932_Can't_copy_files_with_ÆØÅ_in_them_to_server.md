---
title: "Can't copy files with ÆØÅ in them to server"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-24
Hi have problems copying files with ÆØÅ in them to my Ubuntu-Server. Im trying to copy them to a ntfs drive, that is mounted with ntfs-3g. But I can't copy files that contain those letters, can I do anything about that?

---

### Post by energiya on 2007-09-24
The only thing I can think of is renaming. If there are to many files to do it by hand you could try building a shell script that renames the files (sed -e 's/Æ/(ae)/g') and then re-renames them on the ntfs partition (sed -e 's/(ae)/Æ/g'). This might br risky so be sure to test before doing the real thing.

---

### Post by kasperbs on 2007-09-25
yeah there are too many, but there has to be a way around this, because the local NTFS drives can handle the characters without a problem. I have tried to mount using some of the options like:
> default,locale=da_DK.UTF-8
> default, utf8

but it doesn't seem to work

---

### Post by kasperbs on 2007-09-26
Does anyone have any clue as to how this may be solved?

The thing is, the serve is used for backup purposes so I really need it to work as soon as possible

---

