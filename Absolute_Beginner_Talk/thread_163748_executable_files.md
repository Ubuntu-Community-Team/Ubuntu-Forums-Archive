---
title: "executable files"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by TheTux on 2006-04-21
hi

i know this may sound silly but i really need help....i build simple C source code using Anjuta...i can run the executable file from there..the problem is when i double click the file in nautilus...nothing happen...and how to execute the same file in terminal...i can't find the command

And what other IDE for C/C++?? i'm using dev c++ in win but i can only find the old version for linux...any suggestion?

---

### Post by taurus on 2006-04-21
If you want to compile a c program that you wrote in Ubuntu, click Applications -> Accessories -> Terminal.  Assuming that you are in the directory where your program is resided, type
```

gcc program.c <-- to compile it
./a.out <-- to run it

```

---

### Post by mostwanted on 2006-04-21
[QUOTE=TheTux]hi

i know this may sound silly but i really need help....i build simple C source code using Anjuta...i can run the executable file from there..the problem is when i double click the file in nautilus...nothing happen...and how to execute the same file in terminal...i can't find the command

And what other IDE for C/C++?? i'm using dev c++ in win but i can only find the old version for linux...any suggestion?[/QUOTE]

Something does happen, you just don't see it because you haven't launched it in a terminal.

---

### Post by TheTux on 2006-04-22
the ./a.out run the program but actually i've compiled the source code in Anjuta.so the compiled program does not have the .out extension. so i have to recompile it or rename the output file to program.out.

how to make the file executable from the nautilus by just double click it?anyway what is the concept of executable files in linux?what are the extensions?

tq

---

### Post by mostwanted on 2006-04-22
[QUOTE=TheTux]the ./a.out run the program but actually i've compiled the source code in Anjuta.so the compiled program does not have the .out extension. so i have to recompile it or rename the output file to program.out.

how to make the file executable from the nautilus by just double click it?anyway what is the concept of executable files in linux?what are the extensions?

tq[/QUOTE]

Extensions don't matter in Linux, that's a Windows thing. Linux files have MIME-types associated with them, you can just as easily have an executable with a .txt extension or similar. To make a script executable you can right-click on the file in Nautilus and select Properties. There you can change permissions, but your file should be executable from the start of.

The reason you're not seeing your output is because you haven't launched your program from a terminal, as I have already told you once.There's the funny thing about terminal output that it has to be viewed in a terminal :)

I know Windows does this differently, launching the CMD-prompt when you double-click an executable, but that's because Windows doesn't really use command-line output that much. In Linux, pretty much every program has some sort of command-line output, doesn't matter if it's GUI-based. If Linux had the same behavior, then you'd see about 100~ terminals on your screen at any given time.

---

### Post by TheTux on 2006-04-22
ok i think i get it :D
thanks very much

---

