---
title: "how to view a log"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by Lambert on 2005-08-09
From the command line, what commands are used to view a log? What about a command that copies the log to a text document so it can be read by a simple text editor?

---

### Post by PeP on 2005-08-09
from the best to the worst:
for a log file:
most /var/log/bdsalfds
less /var/log/bdsalfds
more /var/log/bdsalfds

for a log like dmesg:
dmesg | most

I do not really understand what you mean by copying a log to a file: all logs are files!

most must be installed first, it can also render man files with colors
try 
export PAGER='most'
and then open a man page (man most)

---

### Post by fng on 2005-08-10
you could also use the command tail for only seeing the last line of a file

tail -n 50 /var/log/messages

---

