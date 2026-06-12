---
title: "Command line syntax"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by woland on 2006-10-31
Well, a really stupid question:
What does a '*' at the end of a file name mean?

---

### Post by bsussman on 2006-10-31
* expands to match any length of characters including none

so st* matches
st
stddd
st##w#w#w#W3
stugga
stbugga

---

### Post by ape on 2006-10-31
If you're talking about the "*" appearing at the end of files during a standard 'ls' command, this denotes that the file is executable.

---

### Post by woland on 2006-10-31
I know that it should be a wildcard, but are there any more meanings?
There is a question in HW about Unix/Linux
```
when it *(*)* appears after the filename ?
```

---

### Post by woland on 2006-10-31
Thanks ape!

---

