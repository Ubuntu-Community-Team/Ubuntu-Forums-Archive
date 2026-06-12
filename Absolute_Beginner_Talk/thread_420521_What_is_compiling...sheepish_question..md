---
title: "What is compiling...sheepish question."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-04-23
err.... what exactly is it? Honestly, I have googled. I thought it just meant installing something and then manually finding all the dependencies. So what is this build-essential thing? And what do people mean by 'compiling a kernel'?

---

### Post by amaroKer on 2007-04-23
Compiling is turning source code (human readable) into binary (computer readable).  Basically, turning text into programs.  If you are installing a program from source code, it needs to be compiled.  That's about all I know.  [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by jfinkels on 2007-04-23
[http://en.wikipedia.org/wiki/Compiling](http://en.wikipedia.org/wiki/Compiling)

Certain languages (like C and C++) require programs to be "compiled" into an object file before they can be executed.

EDIT:

build-essential is a metapackage (a package in the repositories that doesn't contain any programs, just points to other packages) which installs libraries for the C and C++ programming languages, and compilation tools.

A kernel is just one big computer program (really a whole bunch of little ones), so it needs to be compiled, just like any other program.

---

### Post by Fidelio on 2007-04-23
Ok. So why might I want to do that?Which programmes exist only as source code?

---

### Post by jfinkels on 2007-04-23
> **Fidelio said:**
> Ok. So why might I want to do that?Which programmes exist only as source code?

Many programs in the Linux world (including the kernel) are "open source", which means you can download the source code and edit it, if you want (most people don't need to edit source code, ever). But if you have some special function that you need your computer to perform, you could edit the source code for the kernel, compile it, and have yourself your very own flavor of Linux, specifically designed to be efficient in whatever you need it to do.

---

### Post by Fidelio on 2007-04-23
Thanks, I think I get it now. So it's really only for people who know C++ and stuff?

---

### Post by jfinkels on 2007-04-23
> **Fidelio said:**
> Thanks, I think I get it now. So it's really only for people who know C++ and stuff?

Not necessarily, actually! If I download the source code for a program, let's say gaim, just for the sake of example, I can compile it myself fairly simply and enable or disable certain features (developers give the end user a few capabilities without having to edit source code). To compile a program in a *nix system (if you have the correct tools installed) for the most part, you would type something similar to the following commands:
```

./configure --prefix=/usr --disable-whatever --enable-something
make
make install

```
You can try it yourself!

---

