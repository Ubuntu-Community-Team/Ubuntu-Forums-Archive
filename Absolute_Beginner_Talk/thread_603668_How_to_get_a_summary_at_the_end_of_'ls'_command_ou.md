---
title: "How to get a summary at the end of 'ls' command output?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by benton on 2007-11-05
Hi there, I want to know how many files are being listed in the output of the 'ls' command. I've tried reading the 'man' help for the ls command to no avail. Thanks!

---

### Post by benton on 2007-11-05
SOLVED!

ls | wc -l

---

### Post by bhold on 2007-11-05
ls -l | wc -l 

Gives me the number of files listed +1, the extra line is the total line which I think must be the directory file total.

---

