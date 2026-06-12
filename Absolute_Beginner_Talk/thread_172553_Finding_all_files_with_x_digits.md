---
title: "Finding all files with x digits"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-05-08
```
find ./ -name *'%08d'*.foo
```
The above command doesn't work very well.  How do I get it to find all files with 8 digits?

---

### Post by jazzmuzik on 2006-05-08
I put these together quickly. Might not be what you need.

find / -name '????????.foo'

slocate -r \/........\.foo$

---

### Post by tux101 on 2006-05-08
The problem is, those codes will locate anything that has 8 characters (including alphabets).  I need something that looks specifically at 8 digits (numbers).  These 8 digits maybe in between other characters.  That is why I had two asterisks there.

---

### Post by IYY on 2006-05-08
This is ugly, but...

find ./ -name '[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9].foo'

---

