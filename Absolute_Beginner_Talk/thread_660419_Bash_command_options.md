---
title: "Bash command options?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-06
Hello everyone,

I am curious where I can find a list of bash command options. I call them options for lack of a better word.
I am referring to the the part after a command that looks like

ls **-l**

the bold part. What is that called and where can I find a complete list of what they do?

I have seen many like -a, -u, -i, -f etc.

Any help is appreciated. Thanks

---

### Post by taurus on 2008-01-06
```
man ls
```

---

### Post by jken146 on 2008-01-06
Hi!

You're right -- they are called options, and you can find out all about them by reading the man page for the command you're interested in.  For example,  ```
man ls
```

---

### Post by PeterJS on 2008-01-06
Options or flags work to refer to them. To find out about the commands try
```

man *command_name*

```
in this case man is short for manual.

---

### Post by mrphud on 2008-01-06
OK so each command has different options available to it? And all of these are located in the bash manual?

---

### Post by PeterJS on 2008-01-06
Each program has it's own manual that can be read with the man program. There's also a manual for bash itself.

---

### Post by xeth_delta on 2008-01-06
Almost all commands will show you their options if you type:

```
your_command --help
```
and quite often also
```
your_command -h
```

As fellow forum users have indicated you, you can also read the command's manual, which is more complete.

Xeth

---

### Post by mrphud on 2008-01-06
Cool thank you

---

### Post by barney385 on 2008-01-06
[http://www.ss64.com/bash/ps.html](http://www.ss64.com/bash/ps.html)

---

