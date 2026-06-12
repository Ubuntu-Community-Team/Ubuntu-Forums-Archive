---
title: "C Compiler"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by skookamaroo on 2006-05-01
Hey, I am fairly new to linux but I know a wee bit. I need a C compiler, some people have told me to install the kde desktop and it has one built in. but i dont know how to do that, I have searched the forum for an hour and cannot find anything can someone help? are there any other good options for c compilers other than in the terminal? thanks

---

### Post by DSn0wMan on 2006-05-01
I use gcc which auto-magically installs with Ubuntu.

If you dont allready have it, you can get it with

$ sudo apt-get install gcc

But you might be looking for a IDE (Integrated Development Environment) so you dont have to use the command line.

---

### Post by Nequeo on 2006-05-01
[QUOTE=skookamaroo]Hey, I am fairly new to linux but I know a wee bit. I need a C compiler, some people have told me to install the kde desktop and it has one built in. but i dont know how to do that, I have searched the forum for an hour and cannot find anything can someone help? are there any other good options for c compilers other than in the terminal? thanks[/QUOTE]

The terminal's pretty much your only option, as far as open source compilers go. If you haven't already, just type 'sudo apt-get install build-essential' on the command line, and you'll probably get what you need. 

Are you perhaps looking for an IDE that can call a C compiler for you? Maybe take a look at Ajunta. I've never used it, but I think it supports C. 

I don't know what your programming skill level is. But a basic text editor and 'gcc' seem to work well enough for most people not involved in intensive GUI programming. The text editor that comes with Ubuntu supports C syntax highlighting and auto-intending. So does the command line editor, 'vim'. If you learn to use vim, I mean, really *learn* about everything it can do, and practice, you'll be able to program a lot faster than you would with a basic editor. Or even a complicated IDE - depending on what you're programming, of course.

Hope that's of some assisstance.

---

### Post by Sef on 2006-05-01
To compile, build-essential needs to be installed.  

Terminal (Applications > Accessories > Terminal)

sudo apt--get update

sudo apt-get install build-essential

After that you will have gcc and everything else you need to compile installed.

Note: If you are using KDE, change gedit to kate.

---

### Post by not_yet on 2006-05-02
kdevelop is a comprehensive ide :mrgreen:

---

### Post by darth_vector on 2006-05-02
[QUOTE=Nequeo]So does the command line editor, 'vim'. If you learn to use vim, I mean, really *learn* about everything it can do, and practice, you'll be able to program a lot faster than you would with a basic editor. Or even a complicated IDE - depending on what you're programming, of course.[/QUOTE]

vim is the bomb!

---

### Post by skookamaroo on 2006-05-02
thanks alot, yea im just going to use gcc, it seems the easiest. im fairly beginner in C but once i become better (at linux) ill try using vim. thanks guys

---

### Post by Jason_25 on 2006-05-02
vim is the editor, gcc is the compiler.  You can of course still use vim and gcc at the same time.  There are much easier to use text editors than vim, but they are not as programming centric.

---

