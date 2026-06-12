---
title: "Need help at compiling"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by J-Gaming on 2006-06-02
Im total newb at linux. Installed it today 5am, and went to sleep right after that, and that is all of my linux experience..

Anyway, my problem:

when I try to compile c++ with 'make' command I get this error -
```
make: *** No rule to make target `makefile'.  Stop.

```

and thats it.


I searched it but never got actual solution, on google I got some china sites, and on forums didnt find solution.

I hope to fix it soon, thanks :)

---

### Post by Jagot on 2006-06-02
Read this:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by Hanj on 2006-06-02
To compile a project with make you need to have a makefile. Are you trying to compile a program you wrote yourself or one that you downloaded?

If it's a program you downloaded, the makefile seems to be missing. Maybe you're in the wrong directory or maybe there's something wrong with the source package you downloaded. Do you really need the source version, or could you do with a version from synaptic (much easier to install)?

If it's a program you wrote yourself, you can compile it with this line
```

g++ -o nameofexecutable myfile.cc

```
For larger projects, you will want to create a makefile (I'm no expert on this, try to google for tutorials), or use an IDE (check out Anjuta, it's really great).

---

