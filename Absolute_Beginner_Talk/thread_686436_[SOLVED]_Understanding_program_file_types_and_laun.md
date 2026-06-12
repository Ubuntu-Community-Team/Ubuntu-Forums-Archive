---
title: "[SOLVED] Understanding program file types and launchers"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by blaise69 on 2008-02-03
Hi there,

I've noticed in Linux there are at least a couple of 'executable' files to launch programs with, depending on where they're from.

For example in the /usr/bin/ folder application launchers have no discernible filetype, but calling them by name in terminal will load the application, just as launching them from Nautilus will do.

Some programs I've downloaded have a .sh filetype, and it seems they have to be launched using sh infront of them, I'd like to find out more information about what 'executable' filetypes there are and how to use them.  Also there are times when to launch a program I have to use ./ infront of my file.

I'm asking in particular, and this is my main question, because I have created a launcher for my desktop to a program with the .sh extension. It doesn't seem to load though, and I can't see any evidence of something happening either, I am using the sh command in my launcher settings.

I have noticed something else, when I use terminal to open the program, it works successfully when I launch it within its own folder using sh, however, when I try and launch it from outside its folder I get an error, I imagine this is what the issue is.

Any help would be greatly appreciated.

Cheers,

Blaise.

---

### Post by LaRoza on 2008-02-03
Two things, file extensions don't matter (they are there for humans only), and a file must be marked as executable to be run (right click and select properties, or "chmod +x <filename>")

There is a $PATH variable in the shell which hold the directories that are searched for programs.

So when you type "firefox" in the terminal, it launches because firefox is in /usr/sbin which is in your $PATH.

If a file is not in the path, its location must be specified.

To run a program which is in the current working directory, you type "./" in front of it.

Any file (text, binary) can be marked as exectable. For scripts, the first line can have a "shebang" (#!) and the path to the interpreter. For Python scripts:

```

#! /usr/bin/python

```

If a script isn't marked executable and you try to run it, you will get a "Permission denied" error.

You can also run scripts (without marking them executable) by explicitly feeding them into the interpreter, like:

```

$python file.py

```

---

### Post by szymon_g on 2008-02-03
I've noticed in Linux there are at least a couple of 'executable' files to launch programs with, depending on where they're from.

there are, afaik, only 2 general kinds of executable files: scripts and binary files.
scripts use an interpretour (e.g. python, bash, ruby, perl) for working - they have got usually something like that in their's first line:

#!/usr/bin/python (for python's scripts)

For example in the /usr/bin/ folder application launchers have no discernible filetype, but calling them by name in terminal will load the application, just as launching them from Nautilus will do.

you can get filetype of file using 'file' application :> e.g
szymon@linugrat:/usr/bin$ file dpkg
dpkg: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped


Some programs I've downloaded have a .sh filetype, and it seems they have to be launched using sh infront of them, I'd like to find out more information about what 'executable' filetypes there are and how to use them. Also there are times when to launch a program I have to use ./ infront of my file.

sh-files are 'universal' installation-files (eg. producer, instead of making different packages /deb, rpm, etc/ make only one /or two or more- for different architectures/ file so user may download it and install it. but it would by much better, if we could get those application's in deb (or rpm) packages
you put ./ infront of your 'exe file' becouse they are not in your PATH variable, so they cannot be executed by typing eg. sh myfile.sh

I'm asking in particular, and this is my main question, because I have created a launcher for my desktop to a program with the .sh extension. It doesn't seem to load though, and I can't see any evidence of something happening either, I am using the sh command in my launcher settings.

search for adding pathes to PATH variable.

I have noticed something else, when I use terminal to open the program, it works successfully when I launch it within its own folder using sh, however, when I try and launch it from outside its folder I get an error, I imagine this is what the issue is.

so you have 2 choices:
1. always using absolute pathname (eg. /home/blaise/myscripts/my_script.sh)
2. changing $PATH :>

szymon

---

### Post by finer recliner on 2008-02-03
a few things you've noticed:

1) you can launch apps using the ./app method because the first line in those apps include the path to the program they want to be opened with. this is called the shebang line
```
#! /bin/bash
```
it is special for always starting with "#!". linux uses magic numbers to know how to run the application. yes magic numbers is the formal term for this ;-) :
[http://en.wikipedia.org/wiki/Magic_number_(programming](http://en.wikipedia.org/wiki/Magic_number_(programming))

if you're not in the same directory as the app you want to run, you can always supply the full path to the app. example: "/home/user/myApp.sh". the "./" works because "." actually is a shortcut to the current directory you're in. so ./myApp.sh is still

2) your shell always expects you to supply the name of an application a handful of certain directories (/bin, /usr/bin, etc) i honestly dont remember how to check which directories it checks by default right now. if the application is not in one of those directories, you'll need to supply the path of the application yourself (as described above) if you want to be able to launch a custom application from anywhere:
```
$ myApp 
```
then you must copy your file to one of these default directories i mentioned

3) sh is a shortcut to your default shell. in ubuntu, it uses dash by default, but you have other shells that are installed. bash is very popular. be carefull changing your default shell because this may screw with some programs that rely on it.

hope this helps you
enjoy

---

### Post by blaise69 on 2008-02-04
Thanks you've all been a great help.

---

