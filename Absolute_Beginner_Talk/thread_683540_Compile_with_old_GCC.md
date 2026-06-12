---
title: "Compile with old GCC"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2008-01-31
I am getting into Dreamcast development, and the libraries I am using require the GCC 3.0.4 compiler, which I have obtained. Currently, I am using the code::blocks IDE and a newer GCC compiler, but I'd like the option to use the old version as well. Can anyone tell me how to "choose" the compiler revision with code::blocks? It's been a while since I've compiled something from the terminal, and I haven't created a make-file before. Will anyone explain how to do it?

EDIT: Whoops, I only obtained the source, not the pre-compiled binaries. I going to read through the documentation and build it myself, but if anyone can warn me of common pitfalls, I'd appreciate it.

---

### Post by mike1821 on 2008-02-06
In order to compile using an older version of gcc you need to remove the gcc symbolic link from the /usr/bin/ directory and then create a new one using the gcc version you need.

```
rm /usr/bin/gcc
```

```
ln -s /usr/bin/gcc-x.x /usr/bin/gcc
```

Where x.x is the version of the gcc which you want to use.

---

