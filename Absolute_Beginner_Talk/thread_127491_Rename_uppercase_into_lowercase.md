---
title: "Rename uppercase into lowercase"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-02-09
How do I rename the uppercase into lowercase in the file names at once?

So the following:

Ubuntu.foo1
UbUntU.foo2
UBUNTU.foo3

Will all be changed to:

ubuntu.foo1
ubuntu.foo2
ubuntu.foo3

---

### Post by kabus on 2006-02-09
To change all filenames in a directory to lowercase open a terminal and enter this command :

```
for i in *; do mv "$i" "`echo "$i" | tr [A-Z] [a-z]`"; done
```

---

### Post by engla on 2006-02-09
Note that you should probably use 'mv -i', since otherwise UbUNtu.foo might overwrite ubuntu.foo

---

### Post by kabus on 2006-02-09
> Note that you should probably use 'mv -i', since otherwise UbUNtu.foo might overwrite ubuntu.foo

Didn't think of that. :oops:
This should fix it, I hope : 

```
#!/bin/bash
c=0
for i in *[A-Z]*; do
n="`echo "$i" | tr [A-Z] [a-z]`"
if [ -f "$n" ]; then
  n="$n.$c"
  c=$(( $c + 1 ))
fi
mv "$i" "$n"
done
```

---

### Post by DirtDawg on 2008-03-23
This script added numbers to the end of my files. For example, FILE.ZIP turned into file.zip.56. Any way to prevent that from happening?

Thanks

EDIT: I tried the first script also. All I got was the repeated message: '"FILE.ZIP" and "file.zip" are the same file.' Then it left the filenames in all caps. Am I doing something wrong? I simply copied/pasted :confused:

---

