---
title: "No RAR?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2006-04-19
Although I installed Automatix and selected the archiving tools, no RAR seems to be on my system. When I try to open a .RAR file, a message box appears, that this  file format is not supported.

---

### Post by aysiu on 2006-04-19
I guess you could always try going to Applications > Accessories > Terminal and typing ```
sudo apt-get update
sudo apt-get install rar unrar-nonfree
```

---

### Post by Zdravko on 2006-04-19
[[COLOR=#5F2D06]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941"), thanks - it worked!

---

### Post by aysiu on 2006-04-19
[QUOTE=Zdravko][[COLOR=#5F2D06]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941"), thanks - it worked![/QUOTE] Glad to hear it.

---

### Post by MiniJames on 2006-05-23
```
james@jameslaptop:~$ sudo apt-get install rar unrar-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
Package unrar-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar-nonfree has no installation candidate
james@jameslaptop:~$
```

Do you know what the other package might be?


EDIT:

```
james@jameslaptop:~$ sudo apt-cache search unrar Password:
comix - GTK Comic Book Viewer
unrar-free - Unarchiver for .rar files
unrar - Unarchiver for .rar files (non-free version)
james@jameslaptop:~$
```

> unrar - Unarchiver for .rar files (non-free version)

- Got it ;)

---

### Post by blazemiskulin on 2007-01-25
I know I'm coming into this late in the game, but...   I got exactly the same error, and haven't been able to figure out what to do.

I have unrar-nonfree installed (as far as I can tell), but Comix keeps saying that it "can't find unrar executable".

What am I missing here?

---

### Post by Tomosaur on 2007-01-25
What is the output of:
```

slocate unrar

```

and
```

echo $PATH

```?

If you've never run slocate before, you may need to first use
```

sudo slocate -u

``` to build the index.

---

### Post by blazemiskulin on 2007-01-26
Aha.  That was the information that I needed.  It turns out that I had an incomplete/improper install of the unrar.

It's working now.

Thanks.

---

