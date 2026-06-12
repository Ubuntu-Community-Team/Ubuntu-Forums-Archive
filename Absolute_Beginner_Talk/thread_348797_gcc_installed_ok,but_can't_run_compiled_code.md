---
title: "gcc installed ok,but can't run compiled code"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by raequin on 2007-01-29
My c files are compiling fine with gcc, but afterwards I am unable to execute them.  For example:

$ gcc -o hello hello.c
$ hello
bash: hello: command not found

Can you tell me what I'm missing?

---

### Post by jkeyes0 on 2007-01-29
Perhaps try the following?

chmod +x hello
./hello

---

### Post by eightballd on 2007-01-29
Your current directory is not in your PATH.


Try ./hello instead of just hello to execute your program.

---

### Post by raequin on 2007-01-29
That did it.  I thought that "./" was just a generic way of saying, "whatever directory the file's in," so I left it out even though I'd seen it somewhere before (because "hello" was in my current directory).

Thanks a lot.

---

