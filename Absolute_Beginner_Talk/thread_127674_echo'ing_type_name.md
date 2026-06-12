---
title: "echo'ing type name"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-02-09
You know how you enter
```

echo $(basename ~/path/to/file)

```
And it will display the filename?

Well, how do I make it display just the type name (*.foo)?

---

### Post by markd on 2006-02-09
This will give you everything after the last ".":
```
echo ~/path/to/file.typ|sed -e 's/.*\.//'
```

If you want the "*." too, you could do something like:
```
echo "*."`echo ~/path/to/file.typ|sed -e 's/.*\.//'`
```

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=tux101]You know how you enter
```

echo $(basename ~/path/to/file)

```
And it will display the filename?

Well, how do I make it display just the type name (*.foo)?[/QUOTE]
Wasn't sure exactly what you meant when I first read the subject.  The part of a filename after a period in the Windows world is called a " file extension".  In *NIX, extensions are only used by convention.  If you want to guess at the real type of file, you are better off using a command like "file".

---

