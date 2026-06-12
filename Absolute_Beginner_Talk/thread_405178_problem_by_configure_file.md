---
title: "problem by configure file"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by tuannguyen on 2007-04-09
hello,

I want to compile source code, the first i have to run ./configure (right?) but there is no this file. what do i do now to create this file?

thanks for yours answer!
T.

---

### Post by taurus on 2007-04-09
It depends on what you want to compile.  What are you planning to compile anyway?

---

### Post by tuannguyen on 2007-04-09
> **taurus said:**
> It depends on what you want to compile.  What are you planning to compile anyway? 

I want to compile a software "sip_router". I read the file INSTALL, it said, after extract and I run with command "make and then make install". With make command is ok (no error), but when i install that with make install, it can't not (no error, no inform in terminal). I find something talk about that in Ubuntu wiki, it say i have to run ./configure before use command make and make install. ([https://help.ubuntu.com/community/CompilingSoftware)](https://help.ubuntu.com/community/CompilingSoftware)).   

I need really help, thanks in advance
T.

---

### Post by taurus on 2007-04-09
You need to read either the README or the INSTALL that comes with the package.  It will tell you exactly what you need to do to build and install it.  However, you probably need to use the sudo when you want to install it on your system, after running make.

```
sudo make install
```

---

