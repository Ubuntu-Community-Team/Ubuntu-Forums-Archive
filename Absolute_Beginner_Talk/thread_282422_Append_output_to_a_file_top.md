---
title: "Append output to a file top?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by .t. on 2006-10-22
In a BASH script, how would I append the output of a command to the top (rather than the bottom) of a file?

---

### Post by jordanmthomas on 2006-10-22
I'm sure there is a better way, mind you..but would this work?
```
echo text to add >> tempfile
cat oldfile >> tempfile
mv tempfile oldfile
rm tempfile

```

Basically, add what you want into a new file and then append the other file to it.  And move the new file over the old one.

That said, I do not know hardly any bash so there is probably a MUCH better way.

---

### Post by .t. on 2006-10-22
Well, that's what I ended up doing! I also thought there'd be a better way; hence posting here.

---

### Post by bsussman on 2006-10-22
Umm - your instincts are right - data files do not like having stuff shoved in the front.  

Those with a data processing background might suggest adding to the end of the file like normal and piping through sort -r when you want to use the file in most recent first order...:mrgreen:

---

### Post by sumguy231 on 2006-10-22
This isn't any better, but here's what I came up with:
```

#!/bin/sh
tac testfile > testfile_temp;
echo "text to append" >> testfile_temp;
tac testfile_temp > testfile;
rm testfile_temp;

```

---

### Post by .t. on 2006-10-22
Nah. That's not really better. What I was trying to do was to have a Debian changelog update itself, setting the new date as the version, and the same comment as before; so I can have an automagic git daily WINE repository.

---

### Post by David_T on 2006-10-23
If you have something simple and pre-cooked that you want to add, you can do:
```

sed -e '1i\Stuff to add to the top' -i file_in_question

```

But you probably want to do something like this:
```

echo Stuff to add to the top | ./script file_in_question

```

In which case here's something that works in python:
```

#!/usr/bin/python
import sys, os

if len(sys.argv) > 1:
    filename = sys.argv[1]
    if not os.path.exists(filename):
        sys.stderr.write("The file %s does not exist.\n" % filename)
        sys.exit(1)
try: 
    infile = open(filename, "r")
except:
    sys.stderr.write("The file %s cannot be read.\n" % filename)
    sys.exit(1)
file_lines = sys.stdin.readlines() + infile.readlines()
infile.close()
try:
    outfile = open(filename, "w")
except:
    sys.stderr.write("The file %s cannot be written.\n" % filename)
    sys.exit(1)
outfile.writelines(file_lines)
outfile.close()

```

---

### Post by .t. on 2006-10-23
That's great! Thanks. I've gotta learn sed and python...

---

