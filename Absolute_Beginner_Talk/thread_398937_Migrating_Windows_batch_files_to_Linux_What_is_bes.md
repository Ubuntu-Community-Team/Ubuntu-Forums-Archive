---
title: "Migrating Windows batch files to Linux? What is best way to maintain one source code?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-04-01
Hi,
I have written a Windows batch file (.bat) on Windows XP that access IBM DB2 database. It is a pure Windows batch file using db2 command line commands (more or less SQL commands). Program reads input parameters and according to this parameters reads data from database and echo it on screen. So "if" logic with "echo" commands excepting input parameters.

I would like to port this code (about 1000 lines of code) to Ubuntu Linux (and to any Linux possible). I see Linux uses linux script language (.sh), but I don't want to have two versions (Windows batch and Linux sh) of source code to maintaine. I also don't want to install anything but "my code" on target end users computers like Cygwin or something like that. I just want end users install (now they just save the batch file) to there computers.

Program must run in DOS command prompt (no GUI) on Windows and on terminal window on Linux (also no GUI)   - Text mode only.

What is recommended way to make this jobe possible? I have some knowlege about Basic (I have progremed in Visual Basic few years ago).

And tip?

Thanks,
Abcuser

---

### Post by dstew on 2007-04-01
The DOS shell and the Linux shell(s) use different command languages. Only a few commands are the same (dir, echo). Therefore you cannot use DOS batch files in a linux system.

In addition, your database is, I assume, a DOS or Windows program. These programs will not work in linux either.

The only way I see to do what your are trying to do would be to run DOS/Windows programs under Linux in an emulator, like wine.

[http://www.winehq.com/](http://www.winehq.com/)

---

