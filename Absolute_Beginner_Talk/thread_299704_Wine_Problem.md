---
title: "Wine Problem"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by koryo88 on 2006-11-14
I'm having trouble running wine. There are some programs on the server that I need to install but I'm getting this response:

user@computer-name:~$ wine
Wine 0.9.9
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
user@computer-name:~$ wine PROGRAM
wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found
user@computer-name:~$

It's looking for it in Windows folders which I'm obviously not going to have.

Any suggestions?

---

### Post by livingtarget on 2006-11-14
wine PATH_TO_EXE

so for example I want to run the program helloworld.exe in my home directory:

wine /home/lt/helloworld.exe

If it doesn't find it in the URL you give it will look for the 'emulated' windows folder. Which means if you execute "wine PROGRAM" it will look for PROGRAM.exe in the current folder. If it doesn't it will look in the system32 folder for the PROGRAM.exe.

So point wine to the place of your .exe file. It's mostly command based, there's no wine interface to open your .exe files. Although if you are lucky you can double click on .exe files and they will just launch by being passed to wine automatically.

If you want to point to a file that has spaces in it you need to be careful. If there's a space make sure you put the backwards slash before each space in the filename. 

Maybe I'm pointing out the obvious but it's good to remember that most paths in linux are case sensitive as well.

Hope I didn't confuse you there with all the info.

---

### Post by koryo88 on 2006-11-14
Okay, thanks.

I got that the process couldn't be created but I imagine it has to do with the executable rather than wine. Thanks for the info.

---

