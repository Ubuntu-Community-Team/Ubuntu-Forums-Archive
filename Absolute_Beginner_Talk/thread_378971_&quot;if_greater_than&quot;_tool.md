---
title: "&quot;if greater than&quot; tool"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-03-07
Is there a "if greater than" tool in bash?

Say I want to do this:

If the file name is greater than 25 characters, echo 'file name too long!'

---

### Post by po0f on 2007-03-08
newbie22,

I tried doing this in Bash (and I'm sure there's a solution, I just couldn't think of one right now), but here's one in Python:

```
#!/usr/bin/python

import os
import os.path
import sys

try:
    if not os.path.isdir(sys.argv[1]):
        print "Argument not a directory!"
        sys.exit(1)
    else:
        DIR = sys.argv[1]
except IndexError:
    DIR = os.getcwd()


FILES = os.listdir(DIR)

for file in FILES:
    if len(file) > 25:
        print "File name %s greater than 25" % file
    else:
        print "File name %s less than 25" % file
```

Save as whatever.py, run with `python whatever.py <DIR>`.  The above script will check all the filenames in the current directory.  It takes an optional argument, a directory, and will instead check the contents of the specified directory.

As is, it checks **all** the contents of the directory, even directory names.  If you need this to work only on files, let me know.

---

### Post by Arndt on 2007-03-08
> **newbie22 said:**
> Is there a "if greater than" tool in bash?

Say I want to do this:

If the file name is greater than 25 characters, echo 'file name too long!'

'expr' is the program you want. You can do this in a script:

```
if expr length $1 '<' 26 >/dev/null; then
 echo small
else
 echo big
fi
```

---

