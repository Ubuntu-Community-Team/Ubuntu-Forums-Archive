---
title: "lpr fails with MS*.doc files"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by The Dragon Master on 2007-07-24
I have a large number of MS *.doc files which I want to print using a BASH loop. This would not cause me a  problem except that lpr fails to print when I try to use it on an MS *.doc file.  I only have one printer which is set as default and lpr works  with other file formats.  If I do something crazy like 

dave@daves-desktop:~/Desktop$ lpr -# 20  myMSDoc.doc 

and whilst I do that I keep an eye on the printers task window the job appears in the task window with a message to say it is printing and then after a few second the job disapears. lpr clearly thinks it's done it's job. So I'm thinking perhaps I need to convert the *.doc files before sending to lpr or something. How come lpr doesn't work with *.doc files?

all hints welcome
TDM :guitar:

---

### Post by alienexplorers on 2007-07-24
When ever I print a .DOC file I use open office and they print perfectly.  If I try to just print them I get something ressembling alien writing.

---

### Post by The Dragon Master on 2007-07-25
> **alienexplorers said:**
> When ever I print a .DOC file I use open office and they print perfectly.  If I try to just print them I get something ressembling alien writing.

Yeah I know I could start the open office GUI and print from there but I am looking for a non-gui solution so that I can include the printing in a BASH script. There are too many files to want to do this job through GUIs.

TDM :confused:

---

### Post by The Dragon Master on 2007-07-25
OK I get it. the terminal command "openoffice" has a -p flag. So I just have to type

openoffice -p *.doc 

and I print every .doc file in a directory. \\:D/

---

