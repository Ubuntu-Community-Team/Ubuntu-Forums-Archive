---
title: "aclocal woes"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by cogvos on 2007-07-02
Dear all,

Having fought 7.04 all day I am now able to install programmes as a root user. Thank's for all the suggestions as to how to get this far. 

I am now having problems compiling sheepshaver (a Mac emulator) as there is something wrong with aclocal. Now I am not sure what this is, but I am being told that AC_CHECK_FRAMEWORK is under defined. and suggesting i 'extend aclocal'. 
As I am very green at all this I have no idea what this error/warning means and looking on the net dose not help since all the sites descend into tech speak. Equally I have no idea how to extend aclocal, 'cos I have no idea what it is!

Although ./autogen.sh completes (with the above error/warning) make falls over complaining 
./dyngen.exe -o basic-dyngen-ops.hpp obj/basic-dyngen-ops.o
dyngen: ret or jmp expected at the end of helper_op_invoke 

A look around the net showed that someone else had this as well, but they were compiling in windows.

Ideas?

---

### Post by jfinkels on 2007-07-03
> **cogvos said:**
> Dear all,

Having fought 7.04 all day I am now able to install programmes as a root user. Thank's for all the suggestions as to how to get this far. 

I am now having problems compiling sheepshaver (a Mac emulator) as there is something wrong with aclocal. Now I am not sure what this is, but I am being told that AC_CHECK_FRAMEWORK is under defined. and suggesting i 'extend aclocal'. 
As I am very green at all this I have no idea what this error/warning means and looking on the net dose not help since all the sites descend into tech speak. Equally I have no idea how to extend aclocal, 'cos I have no idea what it is!

Although ./autogen.sh completes (with the above error/warning) make falls over complaining 
./dyngen.exe -o basic-dyngen-ops.hpp obj/basic-dyngen-ops.o
dyngen: ret or jmp expected at the end of helper_op_invoke 

A look around the net showed that someone else had this as well, but they were compiling in windows.

Ideas?

Is there a native Linux program we can point you to that might replace a program you are trying to find on Mac? Is there a program in Synaptic Package Manager that is perhaps a Mac emulator? Is there maybe a package out there for this application, so that you don't have to compile it from source?

Have you installed all necessary dependencies for comiling the program?

If the answer to these questions is no, then show us the output when you do ```
./autogen.sh
``` and then when you do ```
sudo make
```. Be sure to wrap the output in the CODE tags in the forum's message editor.

For more information on installing software, take a look at the link in my signature called "Installing software".

---

