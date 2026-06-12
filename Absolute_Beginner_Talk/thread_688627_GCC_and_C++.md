---
title: "GCC and C++?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Patriot1776 on 2008-02-05
Can gcc be used to compile C++ code?  I'm wanting to compile a shared object file from several files of C++ code and this is something I've never done.  I've got experience compiling as I've downloaded programs in source code form before and compiled them, but building a shared object file, from a presumably different language is new.

If this is in the wrong forum, please move it to the proper one.

---

### Post by Cypher on 2008-02-05
No, you want to use "G++" to compile the C++ code, and you can "G++" to compile the C code as well..

---

### Post by emarkd on 2008-02-05
Try 'g++' to compile your c++ code.  It should already be installed.

---

### Post by Patriot1776 on 2008-02-05
Alright, I'm going to look through the g++ man pages now.  All I have are the header files and the cpp files themselves, in two different directories.  They are part of a package somebody sent me on request.

Anybody got a link that explains in easy to comprehend terms building shared object files after compiling the object files?

---

### Post by stevescripts on 2008-02-05
> **Patriot1776 said:**
> Alright, I'm going to look through the g++ man pages now.  All I have are the header files and the cpp files themselves, in two different directories.  They are part of a package somebody sent me on request.

Anybody got a link that explains in easy to comprehend terms building shared object files after compiling the object files?

Maybe something like this?  [http://www.iram.fr/~roche/code/c++/c++_AddNumbers.html](http://www.iram.fr/~roche/code/c++/c++_AddNumbers.html)

Hope it helps ;)

Steve
(yes, the man pages are a bit ... cryptic) :)

---

### Post by Patriot1776 on 2008-02-05
What does the -I option do?  I'm going to invoke g++ in the same directories as the source files.  And also, I don't think I need to tack on "lib" to the name of the shared library, as I'm compiling a shared library file to be used internally by another program, and in any case, I must wind up with a shared library with the name of 'gamex86.so', so I'm putting together a shared library file to be used by a game engine.

---

### Post by Patriot1776 on 2008-02-05
About got it figured out now.  Now I need to get version 3.3 of g++.  Is there a apt-get way of doing this?

EDIT - Nevermind.

---

