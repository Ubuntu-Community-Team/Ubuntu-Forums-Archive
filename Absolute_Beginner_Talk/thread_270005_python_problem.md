---
title: "python problem"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-02
can anyone explain what the command python is for in the terminal.

i dont understand what the point of doing python code in the terminal is for.
whats the point in me downloading stanlys python ide if you can just write program scripts out in a text editor and run them in the terminal.
it dosnt explain this in the tutorials i am reading and all the work im following in the tutorial are telling me to write code in the terminal.

im sooooo confused.

i was learning programming using just basic on windows and it never told me to write code in the dos prompt.
but according to the python tutorials you can write code in there aswell

---

### Post by scrattox on 2006-10-02
> **uk_sphinx said:**
> can anyone explain what the command python is for in the terminal.


It is a python interpreter.  If you pass python code to it, it will run it.

> 
i dont understand what the point of doing python code in the terminal is for.


Well, the point of it is that the program "python" (plus some libraries) is all you need to run python scripts.  So it doesn't matter what fancy IDE you use to create python code, you can pass the code to someone else who doesn't have that IDE and they will be able to run it.
You could think of it as being like the runtime-libraries of MS Visual Basic which you can distribute with your program, but it is much more than that!

> 
whats the point in me downloading stanlys python ide if you can just write program scripts out in a text editor and run them in the terminal.


Well, personally, I would say there is no point in using an IDE.  I do all my programming (in C, C++, Perl and Ruby, mostly) in a simple text editor (vim) and test it from the command line.
Many developers, however, enjoy the advantages that an IDE brings: menus, buttons which compile/run the program rather than having to type the commands each time, online-help, etc.

> 
it dosnt explain this in the tutorials i am reading and all the work im following in the tutorial are telling me to write code in the terminal.


im sooooo confused.

i was learning programming using just basic on windows and it never told me to write code in the dos prompt.
but according to the python tutorials you can write code in there aswell

The fundamental thing you need to know is that all you need to program in python, and many other languages, is a simple text editor and the compiler (in the case of C/C++ etc.) or interpreter (in the case of python, perl, ruby etc.).  The compiler/interpreter is generally something you can run from the command line.

An IDE is just a pretty program which sits on top and does some work for you, but ultimately it's just a clever text editor.  When it comes to compiling or interpreting your code, it just calls the underlying command-line tool.

Here's an example:

Type this at your command prompt

```
cat >my_python_program
print "hello, world\n"

```
(then hit ctrl-D)

'cat' is, amongst other things, the simplest text editor there is.  Whatever you type goes into the "my_python_program" file.

To see what's in there, type:
```
cat my_python_program
```

Now, you can run the program by typing
```
python my_python_program
```

You should now see the ubiquitous "hello, world" message on your terminal.

I've just scratched the surface here, there's a lot more to it (and please don't consider using 'cat' as an editor :) ).
I won't even recommend 'vim' to you, I and many others love it, but it's hard to get into, and you might hate it.  'nano' (for example) is generally a much easier editor to get to grips with.

Have fun programming!  :D

---

### Post by uk_sphinx on 2006-10-02
thanks 

thats cleared up that problem

i didnt realise i could use note-pad to run code of when using basic. tutorials never mentioned it.
i think i would prefer the simple plain text as all the bright colours in stanlys python ide do my nut in.

right back to work!

---

