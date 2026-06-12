---
title: "remove-all-except command"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-01-05
Let us assume that a folder is bloated with random file types.  I would like to remove all the files, except for the *.abc and *.xyz.  How would I do it?

---

### Post by IYY on 2007-01-05
There are far more elegant ways, but here's a method that will work:

rm -i `ls -1 | grep -v '\.**abc**$' | grep -v '\.**xyz**$' | xargs`

ls -1 means list the files in a column.
grep -v means filter only the lines that do not match the following regular expression.
\. is just a period, as in ".abc", but the slash is needed since . has a special meaning in regular expressions.
$ indicates that this expression must appear at the end of the line.
xargs is used to make all of the arguments on one line.

The -i is there to prompt you before every removal. I'd suggest to leave it on there just to make sure that it works as expected. If you remove it, the files will be deleted without asking you.

---

