---
title: "problem with rar archives"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by mykalreborn on 2006-08-25
i just can't seem to get a rar archive open. i've installed ark archiver, xarchiver and i have the ubuntu archive opener and it still doesn't work.
the ubuntu archiver manager says:the archive not suported
the xarchiver:failed to execute child process "rar"(no such file or directory)
and the ark archiver says:the utility rar is not in your path.
what can i do?

---

### Post by LadyDoor on 2006-08-25
Here's what I'd suggest. First, install automatix. Back up your /etc/apt/sources.list file and then open it with a text editor (you will need to use sudo/gksudo to edit this file). Now add this line at the end:

```
deb http://www.beerorkid.com/automatix/apt dapper main
```

Now, in a terminal, type

```
$ sudo aptitude install automatix
```

Automatix should now be installed. Run it either from a terminal or from a menu, if it adds itself to them. This will allow you to install the proper tools to extract and create rar files:  **rar** and **unrar**.

You will need to use them from a terminal, but it should not be too difficult. For example, to extract everything from a rar file (even a multi-part one) to the current directory (and while leaving the rar file(s) intact), you would type

```
$ unrar e filename.rar
```

I hope that helps. If anything was confusing, I would be glad to clarify.
--Door

---

### Post by jrjr on 2006-08-25
.

---

