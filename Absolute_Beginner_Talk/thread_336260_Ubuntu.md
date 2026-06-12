---
title: "Ubuntu"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Nath on 2007-01-11
Hi ppl

I have been trying to use the commandline in ubuntu and I can't do simple things.

I would like to know how to get the current directory to be graphically.

say I am on myhomefolder directory when using the commandline

How do i get to start that directory with a command

---

### Post by taurus on 2007-01-11
Not sure exactly what you mean but you can type this command from a terminal.

```
nautilus
```

---

### Post by jvc26 on 2007-01-11
Sorry slightly confused by your question - you want a graphical representation of your directory I am guessing? If so - are you running a non desktop environment version of ubuntu? (Such as the server edition?) If you're just running the normal one you can go:
```

nautilus /path/to/directory

```
Il

---

### Post by PriceChild on 2007-01-11
or if you mean navigate through folders... then```
cd <<folder>>
```will take you there....
e.g.
```
cd /usr/local/bin/
```

---

### Post by jd65pl on 2007-01-11
Try looking here for some simple commands they have helped me in the past and are useful for everyday bash(ing)
[http://jamie.dumbill.googlepages.com/ubuntucommands2](http://jamie.dumbill.googlepages.com/ubuntucommands2)

---

### Post by Bachstelze on 2007-01-11
Also, a shortcut to have Nautilus open in the current dir without typing the whole path would be :

```
nautilus $(pwd)
```

---

### Post by Enverex on 2007-01-11
> **HymnToLife said:**
> Also, a shortcut to have Nautilus open in the current dir without typing the whole path would be :

```
nautilus $(pwd)
```

An easier one to remember is "nautilus ./"

---

### Post by Pobega on 2007-01-11
You can do that, but I find two things much more efficient:

Either use Alt+F2 to launch apps (nautilus /folder/you/want) or download Midnight Commander (sudo aptitude install mc) which works very good for terminal file management.

---

### Post by MkfIbK7a on 2007-01-11
if you want to do root things in nautalis do
gksudo nautilus
by the way why did you name this thread "ubuntu"?

---

