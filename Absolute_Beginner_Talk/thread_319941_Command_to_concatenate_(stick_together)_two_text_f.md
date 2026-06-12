---
title: "Command to concatenate (stick together) two text files?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-12-16
Hi, I'm not asking how to edit a text file and add a line.

I'm writing a .sh file and I need a command which would append an existing text file and add a line at the end. It would be useful if I also knew how to concatenate two text files. 

Any suggestions are welcome

Thanks

---

### Post by jgordon510 on 2006-12-16
This will do it:

```
echo 'string' >> file.txt
```

---

### Post by ovimunt on 2006-12-16
Hi, does anyone know a command to concatenate (stick together) two text files?

Thanks

---

### Post by invalid on 2006-12-16
```
cat file1 >> file2
```

---

### Post by az on 2006-12-16
> **ovimunt said:**
>  I also knew how to concatenate two text files. 



emma@ubuntu:~$ echo hello > abc
emma@ubuntu:~$ cat abc
hello
emma@ubuntu:~$ echo world > def
emma@ubuntu:~$ cat abc def
hello
world
emma@ubuntu:~$ cat abc def > ghi
emma@ubuntu:~$ cat ghi
hello
world

or even better: 
emma@ubuntu:~$ cat def >> abc
emma@ubuntu:~$ cat abc
hello
world
emma@ubuntu:~$

---

### Post by aysiu on 2006-12-16
I've merged your two threads together, since they're really the same question.

---

