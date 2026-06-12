---
title: "What is a Kernel?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-14
I see this term get tossed around quite often. Can someone explain to me the meaning of what a kernel is?  I also see the term "grub" used very frequently with it.
What are both of these, and what do they do?
Just trying to learn, thanks :)

---

### Post by Inxsible on 2007-11-14
Kernel is the meat of the OS without all the fancy stuff. It is the heart of the OS so to speak.

Grub is the name of the boot loader that helps you in selecting which OS you want to log into, if you have multiple OS'es installed.

[http://en.wikipedia.org/wiki/Kernel_(computer_science]("http://en.wikipedia.org/wiki/Kernel_%28computer_science"))

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

---

### Post by ~chinook~ on 2007-11-14
[IMG]http://tbn0.google.com/images?q=tbn:IDtoNg10QmsGEM:http://www.eglug.org/files/image_store/diagram2-454.png[/IMG]

---

### Post by veerakumar on 2007-11-14
grub is the boot loader
it loads the kernel
Kernel is a program that runs first; after it has been loaded by a boot loader during startup.
e.g. Linux is the kernel.
whereas GNU/Linux is the Operating System (OS) with linux as kernel.

---

### Post by jordank on 2007-11-14
I'm assuming the "shell" part of that diagram is the OS?

---

### Post by llamakc on 2007-11-15
> **jordank said:**
> I'm assuming the "shell" part of that diagram is the OS?

No, but the shell is part of the entire O/S, as is everything in that diagram above HARDWARE.

The default shell on Ubuntu is BASH. It's the environment you are in when you open the Terminal.

---

### Post by jordank on 2007-11-15
Hrmm. that's a bit confusing.
what does bash stand for.
I thought the terminal was basically the raw part of your os.
What's the difference between bash and your kernel?

---

### Post by Inxsible on 2007-11-15
Read up on the two links i gave you earlier and here's one for Bash

[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)

---

### Post by jordanmthomas on 2007-11-15
bash stands for "bourne again shell" and it's a play on words really.  Look up its history (along with a bunch of other linux commands like bison, etc) for a good read.

The kernel is basically responsible for controlling your hardware, processes, and managing memory.  Your shell allows you to communicate with the kernel.  Things you can get from the kernel include (but aren't limited to) things like starting processes and getting information from your hardware.

The OS is the kernel and all the applications that are core to having a functional system.  Note (firefox is not something you'd need to have a functional system, but a shell like bash probably is)

The kernel just loads the other things.  Without a kernel, applications are useless.  Without applications, the kernel is (practically) useless.

> I thought the terminal was basically the raw part of your os.
No, it just provides a layer for the user to interact with the kernel.

---

### Post by jordank on 2007-11-15
Hrmm, the problem is, i think, is that i don't understand the terms used in wiki.  GNU, shell scripts, POSIX, etc.
It's all just a bit intimidating to look at, making it more difficult to learn.

---

### Post by IYY on 2007-11-15
**Kernel:** The part of the operating system responsible for managing resources, That is,   all other software uses it to communicate with the hardware. The user does not interact with the kernel itself in any way.

**Operating System (OS):** A loosely defined term. It is basically the set of programs that are used for other programs to run. Such programs typically include a kernel, various daemons (small programs that run in the background), shells, a filesystem, etc. Some people consider the desktop environment (Gnome or KDE) to be a part of the operating system, while others do not. Some consider only the kernel to be the OS.

**UNIX:** An operating system created by AT&T in the 60's. It was, and still is, very portable and particularly well suited for multiuser (several users logged in at once), multiprocessing (several programs running at once) and networking use. Since AT&T was not allowed to commercially distribute UNIX in the 60's (due to a monopoly lawsuit they lost earlier), it was released without a license and quickly started being used and improved by various universities and companies. Because of this, many commercial and non-commercial versions of UNIX emerged (among the commercial ones is Sun's Solaris and Mac OS X, and the noncommercial ones are the BSDs).

**POSIX:** A set of standards for UNIX-like operating systems. Basically, if a system is said to be POSIX-compatible, it works and is designed similarly to UNIX.

**GPL:** Richard Stallman's GNU Public License is a legal mechanism which allows programmers to ensure that their software's source-code remains freely available. Basically, if a program is released without a license (like UNIX was), it can be extended by other people who in turn lock it down and do not release the code for the improvements. When a program is licensed under the GPL, its source-code is freely available to the public, and can be modified and redistributed, but any changes must also be released under the GPL.

**GNU:** Stands for 'GNU is Not UNIX'. It is a UNIX-like operating system started by MIT hacker Richard Stallman in the 80's. The goal was to have a completely free (licensed under the GPL) operating system. The GNU team have nearly completed their project around 1990, but didn't develop a kernel for it.

**Linux:** A kernel for the GNU operating system written by Linus Torvalds around 1991. Today, when people say Linux they usually mean 'the GNU operating system with the Linux kernel'.

**Shell:** A program the user uses to interact with the filesystem and launch programs. The most basic shells are text-based commandline interfaces, but even a fancy graphical interface like Nautilus in Gnome is also shell (although not often called it). BASH is the 'Bourne Again Shell' (a play on words; it is designed to be similar to the UNIX Bourne Shell).  It's one of the most popular commandline shells nowadays.

**Shell script:** Basically, a shell script is a text file containing a sequence of BASH commands (same as you would type in the commandline). When the file is run, all of the commands execute in sequence. BASH is a very flexible and versatile shell, so the commands can be fairly sophisticated and can resemble small programs. The most important mechanisms in a bash shell are pipes, IO redirection, conditionals and loops. You should learn how to use them if you would like to write your own shell scripts.

---

### Post by jordank on 2007-11-15
So, would this put things in proper terms?

You have your hardware. In order to utilize your hardware, regardless of what it is, you need a kernel.  A kernel is installed when you install your operating system.
if your hardware, is for example, a bedframe, your kernel would be the matress.  Your operating system, on the other hand, is like a bedsheet - somethign that is on top of that mattress that you can interact with.  You never really use your matress without a sheet.  Bash is just a little utility used to call applications from the kernel.  You DO associate with bash.

Am i on the right track? sorry for the odd analogy.  There are 2 beds beside me.

---

### Post by IYY on 2007-11-15
Yes, I think you got it. Except that the 'operating system' would generally be the mattress and sheet combined, since it includes the kernel.

---

### Post by jordank on 2007-11-15
Gotcha.  Thank you, that helps to put things in perspective.

---

### Post by Crypto77 on 2007-11-15
> **jordank said:**
> I'm assuming the "shell" part of that diagram is the OS?
The shell is basically what lets you communicate with the core OS.

---

### Post by hogwartsnigel on 2007-11-15
Thanks Ivy a bloody clear and simple explanation that even i could understand....all this basic stuff really does help newbs like me.

Now what was a computer again?....LOL

Nigel

---

