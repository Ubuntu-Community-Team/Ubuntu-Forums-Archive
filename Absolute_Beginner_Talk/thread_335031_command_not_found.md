---
title: "command not found"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by eng. on 2007-01-09
hi
i was trying to install a program but i receive this error "bash:<command> command not found"
although i have added the path of the program, when i type "which command" i receive nothing. i opened the script in the editor and i found "#!/bin/csh -f" in the first line, i am using bash, is this the problem, and how to solve it?

regards

---

### Post by taurus on 2007-01-09
Command is NOT a command.  More is a command...

```
which more
```
What are you trying to install anyway?

---

### Post by hal10000 on 2007-01-09
if your script uses csh, then you have to install csh---> **sudo apt-get install csh **

Dont worry about using bash, the script is executed in csh automatically if the first line is #!/bin/csh.

---

