---
title: "[SOLVED] RegEx Help"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-11-13
I only know the basic DOS regex (* = all characters all spaces, ? = all characters single space) and am trying to learn Linux regex.

1) Why is it some commands use * as a universal quantifier and regex uses .?

For example if I wanted to delete everything in a directory I would use:
rm *
and not
rm .

At the same time, if I wanted to list everything in a directory it would be:
ls -al | grep .
and not
ls -al | grep *
(I know ls -al lists everything anyway, just using grep to emphasize regex).

______________________________________________

Assume I have a directory with these files:
./
../
file 1 11-13.txt
file 2 11-13.txt
notes 1 11-13.txt
notes 2 11-13.txt
file 1 11-14.txt
file 2 11-14.txt
file 3 11-14.txt

2) Say I want to narrow down to files with the word "file" and "11-13".  Why can't I use:
ls -al | grep .file.11-13.
and instead must use:
ls -al | grep .?*file.?*11-13.?* (actually this fails since 11-13.?* doesn't match properly)

3) How do I batch rename?  Say I want to replace "notes" in all files with "book"?

---

### Post by PointyWombat on 2007-11-14
Hi AncientPC,

. matches one character as in:  /u....u/ will match ubuntu
(? also matches one character, but not in grep)

* matches zero or more of the preceding characters as in: /u*u/ will also match ubuntu

for your example, to narrow down what you're looking for:

ls file*11-13*
or if using grep
ls |grep "file.*11-13"

Further information on regular expressions, including examples can be found [here.]("http://www.regular-expressions.info/reference.html")

To batch rename, that'll require a little script, and there are lots of examples around on how to do that...


PointyWombat

---

### Post by AncientPC on 2007-11-14
Thanks!

Quick question, for the last example (ls | grep file.*11-13) why do you need the period in front of the *?  Why doesn't (ls | grep file*11-13) work?

Edit: nm, found the answer in the link you provided.

---

