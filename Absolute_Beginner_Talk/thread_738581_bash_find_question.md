---
title: "bash find question"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by benevolent on 2008-03-28
Hello there,

I'm writing a bash script for minix, but I'm testing the scrpts, before diving into minix, at ubuntu.. I have this command at ubuntu, which solves my problem, but at minix's [[COLOR="Blue"]**find**[/COLOR]]("http://www.minix3.org/manpages/man1/find.1.html") there isn't the option maxdepth.


This is the "ubuntu" command
**find . -maxdepth 1 -name "name"**


All  I want, is to find all files matching "name" at the current directory _only_, without seeking sub-directories!



I'd appreciate any help,
Thank you in advance

---

### Post by lloyd_b on 2008-03-28
> **benevolent said:**
> Hello there,

I'm writing a bash script for minix, but I'm testing the scrpts, before diving into minix, at ubuntu.. I have this command at ubuntu, which solves my problem, but at minix's [[COLOR="Blue"]**find**[/COLOR]]("http://www.minix3.org/manpages/man1/find.1.html") there isn't the option maxdepth.


This is the "ubuntu" command
**find . -maxdepth 1 -name "name"**


All  I want, is to find all files matching "name" at the current directory _only_, without seeking sub-directories!



I'd appreciate any help,
Thank you in advance

Take a look at this:
```
#!/bin/sh
#
# A very simplified equivlant to "find"
#
# Usage: find.sh {directory {pattern}}
#
# 

if test -n "$1"; then
        DIR="$1"
else
        DIR="."
fi

if test -n "$2"; then
        PATTERN="$2"
else
        PATTERN="*"
fi

for FILE in $DIR/$PATTERN; do
        if test -f "$FILE"; then
                echo "$FILE"
        fi
done
```

This will produce output that looks like what you get from "find", but will not list subdirectories (you can change that by getting rid of the "if test -f..." test), and of course will not recurse.

This *should* work in Minix (but I don't have access to a machine running Minix, so no guarantees on that).

So put this (or a version customized to your taste) somewhere in the PATH, and then replace your ```
find . -maxdepth 1 -name "name"
``` commands with ```
find.sh . "name" 
```.

So just use the shell to create an equivalent to find that does what you want.  The above code should at least get you started...

Lloyd B.

---

### Post by benevolent on 2008-03-28
wow!!

Thank you VERY VERY much for your reply! I'm going to sleep right now, so i'll check this  tommorow, but i'm pretty sure this will work!!


very nice script! thank you again!

jim

---

### Post by Vicariously,I on 2008-03-30
> **benevolent said:**
> wow!!

Thank you VERY VERY much for your reply! I'm going to sleep right now, so i'll check this  tommorow, but i'm pretty sure this will work!!


very nice script! thank you again!

jim

cry

---

