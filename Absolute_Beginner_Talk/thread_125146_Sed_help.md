---
title: "Sed help"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-02-03
Supposely this is the only line in a file:

~/dir1/dir2/dir3/example101.foo

What I want to do is have sed print the text between the last "/" and the last 2 numbers.  The result should say "example1".  Does anyone know how to do it?

---

### Post by markd on 2006-02-03
There might be a more elegant way, but this should do it in two sed's:

sed 's/~.*\///' <filename>|sed 's/[0-9][0-9]\..*//'

the first removes stuff between ~ and / (sed matches the longest pattern, so this should be the last /); the second removes two digits, a '.' and everything after it.

---

### Post by purpleturtle on 2006-02-03
$(basename "~/dir1/dir2/dir3/example101.foo") 

Gets you the filename bit quite nicely.

---

### Post by purpleturtle on 2006-02-03
Or perhaps by using memory parenthesis with sed:

sed 's|.*/\(.*[0-9]\)[0-9][0-9].*|\1|' < thefile

---

