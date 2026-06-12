---
title: "Reliable C Compiler for linux"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Hailogon on 2007-05-07
I'm interested in teaching myself C but am having trouble finding a good C compiler to use with linux. There seem to be so many out there!

Any suggestions?

Much Thanks

---

### Post by justleen on 2007-05-07
i use the GNU c compiler, GCC

---

### Post by Hailogon on 2007-05-07
thanks

---

### Post by steve.horsley on 2007-05-07
Installing package **build-essential** will install the CGG compiler and some other utilities that are often needed. It's all command-line stuff. You might want to check the programmig forum for recommendations of which graphical IDE to use - the question gets asked very frequently so a search should find answers quickly.

---

### Post by sloggerkhan on 2007-05-07
If you want somewhere to start for simple code, geany is a lot like textpad on windows. You will probably want to change the compile command for c so that it link the math library, though.

---

### Post by srt5 on 2007-05-07
We did some C last year at university, they recommended the GCC compiler. If your new to programming in general then you may want to consider "C in a Nutshell" it's a good book for introducing the language and it's features, and it's easy to use as a quick reference guide too :)

---

### Post by rich.bradshaw on 2007-05-07
Yeah, gcc is the best standard compiler.

sudo apt-get build-essential

will get it,

cc sourcefile.c -o outputprogram

will run it.

---

