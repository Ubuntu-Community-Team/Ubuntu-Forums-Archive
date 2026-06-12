---
title: "problem with gdb"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by sickterm on 2008-03-03
hi all,

actually I wanted to backtrace a bug I got in pidgin. for that I first followed the instructions ("https://wiki.ubuntu.com/DebuggingProgramCrash") to install all the necessary programs. After that I tried to follow these instructions: "https://wiki.ubuntu.com/Backtrace". I started my pidgin as usual (i'm the owner of it, so I did not log in as root). But i always get a errors in gdb::

"fran@fran-desktop:~$ pidof pidgin
12201
fran@fran-desktop:~$ gdb 2>&1 | tee gdb-pidgin.txt
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
(gdb) handle SIG33 pass nostop noprint
Signal        Stop      Print   Pass to program Description
SIG33         No        No      Yes             Real-time event 33
(gdb) set pagination 0
(gdb) attach <PID>
Illegal process-id: <PID>.
(gdb) continue
The program is not being run.
(gdb) backtrace full
No stack.
(gdb) fran@fran-desktop:~$"

Can anyone help? I tried to google but I couldn't find much about it.. Thanks :)

---

### Post by Cypher on 2008-03-05
For the "attach" command, you should use "attach 12201" which is the PID (Process ID) you got back from the "pidof" command.

---

