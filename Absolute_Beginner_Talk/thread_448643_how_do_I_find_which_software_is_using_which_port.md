---
title: "how do I find which software is using which port?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by joeserel on 2007-05-19
Hi,

I would like to know if there is a handy command-line tool (like Port Explorer) to find out which program is listening to which port in Ubuntu.

Thanks.

Joe

---

### Post by halitech on 2007-05-19
netstat should give you a listing of all connections to your computer. open a terminal and type

```
netstat | less
```

that way you can scroll through it as it will also give you all the local ports that linux uses

---

### Post by Bachstelze on 2007-05-19
*netstat*. Read the man page for info about the options it takes.

---

