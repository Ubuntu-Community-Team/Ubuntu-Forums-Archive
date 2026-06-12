---
title: "File path"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by nishanthaMe on 2007-08-24
I want to get the absolute path of any file in the file system using a C programme.Can anybody have an ide,just let me know
                                      Thanks

---

### Post by jay4e on 2007-08-24
if your writing the program you can use unix shell commands in c code, ie locate, find, pwd, ls, ect.  optionally you can write a separate shell script and invoke it from your c program and read the output into the program.  this will allow for easier editing by users.

more info [http://heather.cs.ucdavis.edu/~matloff/unix.html](http://heather.cs.ucdavis.edu/~matloff/unix.html)

---

### Post by nishanthaMe on 2007-08-31
It works.Thank You very much!

---

