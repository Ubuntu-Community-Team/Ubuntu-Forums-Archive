---
title: "I need a program like C++,"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-07-02
any programs that will be as good, or better??:cool:

---

### Post by raptros-v76 on 2006-07-02
wait. c++ is a language. could you please clarify what you want?

---

### Post by wannabesurfer on 2006-07-02
in windows, I use visual studio C++ to program, I was wondering if there is an equilant to this program available

---

### Post by lurchi on 2006-07-02
What about Kdevelop?

---

### Post by jchau on 2006-07-02
Well, I doubt that visual c++ will ever be ported to GNU/Linux, however, if you need a c++ compiler, try "g++".  For editing source, you can use any text editing program like vi, nano, kate, emacs, gedit, etc..  To debug, you can compile with the debug flag using g++ and use "gdb" as the debugger.  

Enjoy!

---

### Post by Hanj on 2006-07-02
The two most common IDE:s are Anjuta (for Gnome) and KDevelop (for KDE). I personally like Kdevelop much more, so I use it in Gnome too. They're both in the repositories, so just use Synaptic to install them. 

Note: if you're trying to run Kdevelop in Gnome you may get some problems (plugins crashing and such). Installing the package kdebase fixed all this for me.

---

### Post by mscman on 2006-07-02
There are a few that come to mind, you'll just have to try them out and find which suits you best.

Anjunta IDE
Eclipse -- Java-based, but has a C++ plugin
SciTE Text Editor -- I use this for programming in Perl, although it will do syntax hilighting for C and many other languages and also supports macro functions.

Finally, you could simply develop the .c and .h files in a folder using vim, emacs, nano, gedit, or any other text editor (even SciTE as mentioned above) and compile/test the program from the terminal using the command:
```
g++ <name of source file> <name of output file>
```

More info on compiling via command line can be found by viewing the man pages for g++

---

### Post by jchau on 2006-07-02
[QUOTE=mscman]
```
g++ <name of source file> <name of output file>
```
[/QUOTE]
You'd probaby have a bit of trouble compiling with that command.  try:
```
g++ -o NameOfCompiledProgram sourcefile0 sourcefile1 sourcefile2 tosourcefileN
```

---

