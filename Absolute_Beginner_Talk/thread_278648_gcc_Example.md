---
title: "gcc Example"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by newbie-wan on 2006-10-16
I am an absolute novice when it comes to unix and its derivatives so I apologize in advance for my stupidity.

I've successfully installed ubuntu and gcc, etc.  I am now attempting to build a library from some c files.  The problem I am having is in using Gnome terminal to run gcc and at the same time access the source files which I have in the file system.  I know that the command line should look something like:

gcc -c -lm FILENAME.c

however, i don't know how to specify the directory where the files are.  In terminal i attempt to change to that directory but i cannot figure out how to do it.  Again, I am sorry.  I realize that this is elemental stuff but I can't figure it out.

Thank you for your assistance and time.

---

### Post by K.Mandla on 2006-10-16
The change directory command is cd, so for example

```
cd /media
```
will take you to the /media directory, and 

```
cd ~
```
will return you to your home directory.

As far as parameters for gcc, I guess you could check the man pages for gcc with

```
man gcc
```
or try some searchable man pages [here]("http://www.die.net/doc/linux/man/"). Hope that helps. :)

---

### Post by localuser on 2006-10-16
Newbie-one,

Don't feel bad about not knowing anything about gcc.  This is one of those topics that is *very* difficult to explain in a short forum thread.  Its going to take some research on your part.

gcc is a compiler.  It "converts" programs written in high-level languages like c into code which the machine can understand.  Naturally, knowing how to use gcc is something that requires some learning.

You say that the command should look "something like this"...the problem is that even a small change in the command arguments (those things after the dashes) can alter the end result.

Without knowing exactly what you're trying to do, it may be difficult to answer your question as to what the command should be.  If you are a beginner at this, then I assume that you are following some instructions which ask you to use the compiler.  Where did you get the command that you wrote?  Are you copying it from somewhere?

~Cheers

---

### Post by ReaderRat on 2006-10-16
For Reference:....
Terminal Commands - The Shell Game
         [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
                  - Alphabetical
         [http://www.ss64.com/bash/](http://www.ss64.com/bash/)
                  - Alphabetical - Search
         [http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)
                  - Common Admin
         [http://www.debianhelp.co.uk/commands.htm](http://www.debianhelp.co.uk/commands.htm)
gcc command:
         [http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=g/gcc](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=g/gcc)

---

### Post by newbie-wan on 2006-10-16
Thank you all.  You know what?  It was the direction of the slash that was getting me.  DUH!

Now another issue.  I've created objects and am trying to link them into a library.  I am now getting errors that indicate no recognition of some of the math functions contained in math.h (i. e. pow, log10, pow, floor, etc.).  I did create the objects using the -lm flag but something is amiss.  Any ideas?

Object creation line---

gcc -c -lm source.c

Library creation line---

gcc -o filename *.o

Thank you again for your kind help.  I've got to get out of my old "DOS" mode and think real computing.

---

### Post by newbie-wan on 2006-10-16
I've searched the file system and do not see math.h.  That doesn't seem right to me.  Why wouldn't that file be present?

---

### Post by ReaderRat on 2006-10-16
> **newbie-wan said:**
> I've searched the file system and do not see math.h.  That doesn't seem right to me.  Why wouldn't that file be present?
Have you searched all the repositories?....
Repositories - Adding Extra:
          [https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)
Repositories - All You Need To Know
          [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

