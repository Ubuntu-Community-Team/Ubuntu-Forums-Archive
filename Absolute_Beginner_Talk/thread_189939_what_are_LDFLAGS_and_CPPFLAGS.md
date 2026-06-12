---
title: "what are LDFLAGS and CPPFLAGS"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by ph7klw on 2006-06-05
Do u know where can I find the meaning of the command over the internet?

---

### Post by darkali on 2006-06-05
They're not programs, they are merely options inside a file generally named 'Makefile' used by 'make' (which is a program to build software).

What 'make' do is tell the compiler to use these option when compiling a program. You can also name then anything you like because all 'make' do is to substitute then and parse then to the compiler.
The CPPFLAGS are for objects, see:
[http://en.wikipedia.org/wiki/Object_code](http://en.wikipedia.org/wiki/Object_code), for more info.
And LDFLAGS are for the linker, see:
[http://en.wikipedia.org/wiki/Linker](http://en.wikipedia.org/wiki/Linker), for more info

So for example inside a 'Makefile' you could see:
CPPFLAGS:= -Wall

The option '-Wall' tell the compiler to show all warnings (possible code errors).  
For more about make : [http://en.wikipedia.org/wiki/Makefile](http://en.wikipedia.org/wiki/Makefile).

Hope that helps

---

