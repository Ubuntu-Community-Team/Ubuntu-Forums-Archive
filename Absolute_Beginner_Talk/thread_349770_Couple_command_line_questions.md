---
title: "Couple command line questions"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-01-30
How do I find zero length files in a directory using bash?

Also how can I rename a bunch of *.java files to *.java.bak in bash?

---

### Post by Hanzerik on 2007-01-30
For the rename issue:

```

for i in *.java; do mv "$i" "$i.bak"; done

```

---

### Post by po0f on 2007-01-30
syalam,

[quote=syalam] 	How do I find zero length files in a directory using bash?[/quote]

```
[FONT="Courier New"]$ find . -type f -size 0[/FONT]
```

The above works in the current working directory.  To specify a directory, replace the dot with the directory.

---

### Post by p!=f on 2007-01-30
> **syalam said:**
> How do I find zero length files in a directory using bash?

To find empty files in your home type
```

find ~ -size 0c

```
To find empty files and directories in your home type
```

find ~ -empty

```
Look at man pages for more options.

> **syalam said:**
> 
Also how can I rename a bunch of *.java files to *.java.bak in bash?
There are plenty of options how to do this. Here's the very basic example:
```

for file in *.java; do
     mv $file ${file%java}java.bak
done

```
There's also 'rename' command.

---

### Post by bruenig on 2007-01-30
It is much simpler to use rename
```
rename 's/.java/.java.bak/' *.java
```

---

