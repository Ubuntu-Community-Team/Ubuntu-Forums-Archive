---
title: "[SOLVED] Edit a file..."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2008-01-26
\usr\share\games\singularity\techs.txt

I cannot open it from Gnome, I need to edit it so I can alter this game to suit my liking.  Sez I need to be root.  How would I go about doing this from the command line? Sudo *fill in the blank here* I assume.  I want to send it to text editor so I can alter item costs...  YES I AM A FILTHY ROTTEN CHEATER HELP ME TAKE OVER THE WORLD!  :D

---

### Post by mouko on 2008-01-26
sudo gedit [file]

---

### Post by LaRoza on 2008-01-26
> **mouko said:**
> sudo gedit [file]

Don't use sudo, use:

```

gksudo gedit

```

Might want to backup the file first.

Press Alt + F2 and enter the command.

---

### Post by LookTJ on 2008-01-26
> **mouko said:**
> sudo gedit [file]
For GUIs, it's better to use:
```
gksudo gedit file
```;)

---

### Post by nemilar on 2008-01-26
```
gksudo gedit [filename]
```

or just 

```
sudo gedit [filename]
```

---

### Post by LaRoza on 2008-01-26
> **nemilar said:**
> ```
gksudo gedit [filename]
```

or just 

```
sudo gedit [filename]
```

Don't use sudo.

---

### Post by Epic Plecostomus on 2008-01-26
Quick turnaround.  Thanks everyone.

---

