---
title: "| that thing when used in the terminal"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by mike941 on 2008-02-14
| what does that thing do and on a similar note what does a semicolon mean? You might want to consider adding this to the command line tutorial for gutsy. Thanks in advance!

---

### Post by spiderbatdad on 2008-02-14
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

---

### Post by emarkd on 2008-02-14
| is the pipe.  It "pipes" the output from the first program into the second one.  For instance:

```
ps -e | grep firefox
```

uses ps to lists all programs running on the computer and then pipes that output to grep, which searches for firefox.

The semicolon separates two programs.  The first program will run, then when it exits the second one will run.

---

### Post by hyper_ch on 2008-02-14
And when you use the > you can save the output to a file:

```

ls -al > ~/Desktop/output.txt

```

This will create an output.txt file on your desktop and contain the output code from "ls -al"

---

