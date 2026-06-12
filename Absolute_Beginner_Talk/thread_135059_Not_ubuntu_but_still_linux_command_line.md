---
title: "Not ubuntu but still linux command line"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by StueyB on 2006-02-23
Well I figured id ask. I have a remote FreeBSD machine and I need to locate ALL the files that have the string 838313 in the html source code and flag the file into a listing file that I can then work on.

I know I have to use the find command, but more than that im stuck, ive toyed for a while with it, but it just seems to list every file

I know its not ubuntu, but not everywhere is as friendly as here !

---

### Post by engla on 2006-02-23
Well grep should be able to help you...

If you go to your top directory (the one you want to search in [recursively]) this 'grep' should help you

grep -R "838313" *

if you just want the filenames, use -L too

---

