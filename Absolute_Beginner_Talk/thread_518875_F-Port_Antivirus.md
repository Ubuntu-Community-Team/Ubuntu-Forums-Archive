---
title: "F-Port Antivirus"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-06
While scanning a file using F-Port, i get the following output.....

Virus scanning report  -  6 August 2007 @ 21:46

F-PROT ANTIVIRUS
Program version: 4.6.8
Engine version: 3.16.16

VIRUS SIGNATURE FILES
SIGN.DEF created 3 August 2007
SIGN2.DEF created 3 August 2007
MACRO.DEF created 3 August 2007

Search: /ICC3.exe
Action: Report only
Files: "Dumb" scan of all files
Switches: -ARCHIVE -PACKED -SERVER

Error on reading /ICC3.exe

Results of virus scanning:

Files: 0
MBRs: 0
Boot sectors: 0
Objects scanned: 0

Time: 0:00

No viruses or suspicious files/boot sectors were found.

CAN SOMEONE EXPLAIN THIS OUTPUT TO ME

pkj

---

### Post by Rocket2DMn on 2007-08-06
I haven't heard of F-PROT, but it's trying to run a .exe file which is a windows executable and cannot be run under linux without a program like wine.  Are you using wine to run this, if so, why?  There is no need to have a virus scanner on your linux machine since viruses are not a problem for linux users.
The program said it was unable to run ICC3.exe, most likely because of the above explanation.  Just get rid of the virus scanner, only keep one installed on your windows partition if you have one.

---

### Post by por100pre1 on 2007-08-06
There are many causes for that, for example, that you don't have permissions to access the file. Try adding this switches to the command: -COLLECT -REPORT=/home/YOURUSERNAME/.xfprot/xfprot.log -AI

---

### Post by Rocket2DMn on 2007-08-06
It looks like there is a linux version of this program.  Why it is trying to run an .exe file is still beyond me, but assuming you have everything setup correctly and DO actually want to run a virus scanner (for whatever reason), you might need to run the program with root privileges.  If you are running the scanner from terminal, preceed the command with "sudo " and type in your password when prompted, and this will run the scanner with superuser privileges.  If the program has a graphical interface, use "gksudo " instead.

---

### Post by por100pre1 on 2007-08-06
Check this Info on [ICC3.exe]("http://spywarefiles.prevx.com/RRDHHB43207226/ICC3.EXE.html").

---

