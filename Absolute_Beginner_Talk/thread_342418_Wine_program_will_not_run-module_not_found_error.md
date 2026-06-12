---
title: "Wine program will not run-module not found error??"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-20
When I type" wine PROGRAM" into terminal I get "wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found". Do I have to download something else to use the program. (Don't laugh too hard, just a shiny newb trying to figure this stuff out:roll: ) Thanks for the help.

---

### Post by rai4shu2 on 2007-01-20
If you have already run "winecfg" in a console, then you may do things like this:

wine notepad.exe

Note that notepad.exe is a program that is installed in your ~/.wine/drive_c/windows/ folder.

A program doesn't need to be in the windows folder. It can be run from anywhere, but it does need to exist.

Here's another tip. To use .bat files in Wine, type:

wine start FILE.bat (where FILE is the name of the batch file)

---

### Post by www.rzr.online.fr on 2008-05-15
IICR, "Module not found" message is also printed on missing dll, need to confirm too

---

### Post by MaindotC on 2008-05-25
I moved googletalk-setup.exe into the folder specified by rai4shu2 and it installed (albeit unsuccessfully).  Thanks for the suggestion!

---

