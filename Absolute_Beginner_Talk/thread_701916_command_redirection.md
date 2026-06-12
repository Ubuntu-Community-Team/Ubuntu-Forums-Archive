---
title: "command redirection"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by dork5002002 on 2008-02-19
I need help with a little command redirection

I know how to redirect output to a file using ">"
I know how to append output to a file using ">>"
I know how to display output from a command and redirect it to a file using "| tee"

but how do I display output to the screen and append it to a file.

---

### Post by lloyd_b on 2008-02-19
> **dork5002002 said:**
> I need help with a little command redirection

I know how to redirect output to a file using ">"
I know how to append output to a file using ">>"
I know how to display output from a command and redirect it to a file using "| tee"

but how do I display output to the screen and append it to a file.

Use the "-a" option of tee:
```
ls | tee -a dirlist.txt
```
will display the ls output, and append it to the file dirlist.txt.

Lloyd B.

---

### Post by amohanty on 2008-02-19
command | t **-a** filename

---

### Post by dork5002002 on 2008-02-19
I guess I was just too caught  up in ">" and "|" to remember to check the extra tags of the tee command.:oops:

---

