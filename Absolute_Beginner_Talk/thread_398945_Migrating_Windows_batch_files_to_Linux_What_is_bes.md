---
title: "Migrating Windows batch files to Linux? What is best way to maintain one source code?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-04-01
Hi,
I have written a Windows batch file (.bat) on Windows XP that access IBM DB2 database. It is a pure Windows batch file using db2 command line commands. Basic is read some data from database and echo it on screen. So "if" logic with "echo" commands.

I would like to port this code (about 1000 lines of code) to Ubuntu Linux (and to any Linux possible). I see Linux uses Linux script language (.sh), but I don't want to have two versions (Windows batch and Linux sh). I also don't want to install anything but "my code" on target end computers like Cygwin or something like that. I just want end users installs (now they just save the batch file) to there computers.

Program must run in DOS command prompt (no GUI) on Windows and on terminal window on Linux (also no GUI).

What is recommended way to make this jobe possible? I have some knowledge about Basic (I have programed in Visual Basic few years ago).

And tip?

Thanks,
Abcuser

---

### Post by Spr0k3t on 2007-04-01
For what you are doing, I think you would need to go with something like Python.  The source would be the same from platform to platform.  The problem, you would need to port the dos batch files over to python.

---

### Post by Spr0k3t on 2007-04-01
This appears to be a double post, asking for a mod to merge the threads.

---

### Post by Lary Grant on 2007-04-01
If you are accessing a DB2 database, you should definitely look into translating your BAT file into Perl, because Perl has an excellent module called DBD::DB2 that was developed by IBM.  It is pretty simple to use and is much better than using the "db2" command line program.  With DBD::DB2, you don't need to parse text output ... it returns the result sets from your SQL in proper data structures, just like if you used C or Java.  Let me know if you need help with it.

It works with Perl's general-purpose DBI module.  Here is a tutorial on DBI:
[http://www.perl.com/pub/a/1999/10/DBI.html](http://www.perl.com/pub/a/1999/10/DBI.html)

The tutorial uses Oracle, but just substitue DB2 with Oracle, and it should be the same.

---

### Post by abcuser on 2007-04-02
Hi,
are you sure Perl program will run on Windows/Linux **without installing** some kind of Perl server on computer? I need to post this program to multiple Windows (now also Linux) end user computers - so it must be zero installation option, like batch file transfered by e-mail. Users can save the file to destination folder and execute it. I just can't afford to have some installation, it would be too complicated to end users.

This program also must run on servers where no software is allowed to be installed. I must also write a solution for Suse Linux running on IBM mainframe zSeries computer architecture (not Intell at all). So I can't imagine to install some kind of software on production mainframe computer.

So I see following options:
1. recode all batch file to Linux sh script or have some "magic" tool to convert it automatically.
2. create some kind of executable file (probably one for Windows and one for Linux) - in this kind of solution I am little bit afraid to have multiple execution files on Linux because of multiple architecture (mainframe, Intel).
3. use some kind of independent script language with just copy/paste some libraries (no install just copy/paste)

Thanks,
Abcuser

---

### Post by freebird54 on 2007-04-02
If the logic is as plain vanilla as you state, then a quick 'parser/translater' in Python should be trivial to write.  Input = DOS batch and ouput = sh script.  For that matter you could write it in shell script itself - and feed it the DOS batch file as input.  How often does the batch need to be modified?

---

### Post by abcuser on 2007-04-02
Hi,
I don't think it is so simple. I have studied some sh files and I see the syntax is quite different. So any simple dos input - sh output is difficult to write. I think it would be less time spend to write the sh file from beginning. I don't see the problem of writing this commands - I just don't like the idea to have two source code programs to maintain, because of two source code development, two testing systems, two documentation instructions etc. I hate this kind of solution. The simplest way it would be to have some kind of "magic tool" to convert my Win-batch code to sh code automatically without any code modification.

This batch file changes about ones per two weeks or less. But it can be changed two or more times a day if some new function is involved and some bugs are in it.
Thanks.

---

### Post by freebird54 on 2007-04-02
The syntax may be different, but the capabilities are not less.  It is not at all uncommon for a script to read and parse another file for its instructions - after, even DOS can parse what you've given it!

What I propose is either a script that can run a DOS batch directly - or a converter written in Python or script that you 'one-time' it through before shipping it to *nix sites.
Is there a representative piece of (non-proprietary) example code you could attach?  I'll bet there are more than a few here who can put something together for you quite quickly....

Or, one could pull out the old QBasic 4.5 disks and convert it on the Win side if you prefer!! :D

---

### Post by abcuser on 2007-04-02
Is there any web site to do conversion beetween win-batch and lin-sh?

---

### Post by freebird54 on 2007-04-02
I am afraid I don't know of any - I'd have to google/yahoo it too.  It really doesn't sound like it would be a very difficult thing to do.  It certainly wouldn't be hard to find an example parser as source code out there...

There are also programming sites out there where people hope that problems get posted for them to solve!  Don't know if this is tough enough for them though.....

---

### Post by abcuser on 2007-04-02
Hi,
I have written couple of line of sh code and I am suppried that running sh script on Cygwin and on Linux doesn't do the same thing. It looks like Linux for each sh executed makes it's own environment. I don't like this - I would make my script useless...
Ok, I will try to find out any other solution. Thank you very much for help.
Abcuser

---

