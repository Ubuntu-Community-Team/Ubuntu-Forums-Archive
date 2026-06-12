---
title: "store date in variable"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-18
how would I store the output of a command into a variable in BASH. for example if I wanted a to hold a string value of the current date using the date command?

---

### Post by Arndt on 2007-10-18
> **ssaamon said:**
> how would I store the output of a command into a variable in BASH. for example if I wanted a to hold a string value of the current date using the date command?

```
$ x=`date`
$ echo "Date is $x now."
Date is Thu Oct 18 09:32:03 CEST 2007 now.

```

---

### Post by tkharris on 2007-10-18
If you're planning to use this for a backup program or similar and are writing files with the data in the name of the file you may want to use epoche time ( no spaces which is better for file names, and ls will show the newst first assuming the directoy is filled with files with the same name besides the date. )

date=`date +%s`

---

