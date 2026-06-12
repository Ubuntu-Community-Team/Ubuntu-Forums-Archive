---
title: "help with command executables (gcc?), please!!"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-08-28
I have been using Ubuntu from a while now, but I noted that, in Windows, if you have a program (compiled in C, but for those who don't know it its actually a hello-world program) like this:

```

int main()
{
 puts ("Hello, world!") ;
 getchar() ;
}

```

And you execute double clicking its icon, a terminal windows opens and executes it. Why does this not happen in Linux, or I need to put a special termination on it for terminal to open?

EDIT: Im sorry, my question was no clarified at all. I mean that I compiled the file, made an executable, but this executable, since its text only, had to be executed from terminal. I was asking if there was any way of executing it from Nautilus (like in windows)

---

### Post by Mornedhel on 2007-08-28
Hello again.

Are you familiar with the permissions system on UNIX OSes ? Your compiled program needs to be executable by your user. You should also run text-only programs straight from the console instead of double-clicking them in Nautilus. For instance, in a console :

cd my_helloworld_program
chmod 744 a.out
(makes a.out readable, writable and executable for you, readable only for the rest of the world)
./a.out
(runs a.out)

---

### Post by Fixman on 2007-08-28
> **Mornedhel said:**
> Hello again.

Are you familiar with the permissions system on UNIX OSes ? Your compiled program needs to be executable by your user. You should also run text-only programs straight from the console instead of double-clicking them in Nautilus. For instance, in a console :

cd my_helloworld_program
chmod 744 a.out
(makes a.out readable, writable and executable for you, readable only for the rest of the world)
./a.out
(runs a.out)

Well, you actually didn't understand well my question. It was regarding this part of your post:

> You should also run text-only programs straight from the console instead of double-clicking them in Nautilus
I was asking if there was any way of doing so

---

### Post by dwhitney67 on 2007-08-28
You need to compile the source code using gcc.

For instance:
[FONT="Courier New"]
$ gcc hello.c[/FONT]

This produces an "a.out" file that is the executable.  To run it on command line, just type:

[FONT="Courier New"]$ ./a.out[/FONT]

If you do not like the a.out name, you can set what the executable name will be when running gcc like:

[FONT="Courier New"]$ gcc hello.c -o hello[/FONT]

Then just run './hello'

---

### Post by dwhitney67 on 2007-08-28
> **Fixman said:**
> Well, you actually didn't understand well my question. It was regarding this part of your post:


I was asking if there was any way of doing so

yeah... just go to your desktop, right click to create a launcher, then fill in the blanks.  The "command" is the program you want to execute.  if it is a text-based application (eg. the hello-world program) then run it as an Application in a Terminal.

---

### Post by Mornedhel on 2007-08-28
Then instead of the ./a.out part, once the permissions are given (you can also do that in Nautilus, right-click on the file, Properties, check Execute in the Permissions tab), you can double-click a.out.

As a side note for dwhitney : I do know how the permissions work in UNIX, I simply wasn't aware that at compilation, files were created with execution permission by default. I code mostly in Perl and thus I have to chmod my files to executables after touch-ing them (I prefer to use the shebang rather than call perl explicitely). The 'typical' permissions, for me, are rw-r--r--, as I mostly work with text files. Fixman seemed to want to know how to make his program executable (at least, I thought he did, which was in fact not the case). As far as I know, double-clicking a non-executable file in Nautilus (not a launcher - I wasn't talking about the launcher, rather about the actual executable - would you create a launcher for each program you write, and place it on the desktop ?) tries to open it with the relevant utility, and double-clicking an executable file may bring up a console for a text-based program (and it may not - I never tried double-clicking text-based executables...) which could close again once the program is finished. Apparently it does not. My mistake.

---

### Post by dwhitney67 on 2007-08-28
> **Mornedhel said:**
> Then instead of the ./a.out part, once the permissions are given (you can also do that in Nautilus, right-click on the file, Properties, check Execute in the Permissions tab), you can double-click a.out.
What are you writing about?  Right click on what?  When the a.out is generated is already has execute permission for the user who created the file, and for the "group" and for the "world".  Those in the "group" (with the exception of the user) and "world" cannot delete the file, because for them the file is read-only.

The typical permissions look like:

[FONT="Courier New"][INDENT]-rwxr-xr-x[/INDENT][/FONT]

Please stop spreading misinformation.  It is obvious that you really do not fully comprehend the workings within Linux/Unix at this time.

---

