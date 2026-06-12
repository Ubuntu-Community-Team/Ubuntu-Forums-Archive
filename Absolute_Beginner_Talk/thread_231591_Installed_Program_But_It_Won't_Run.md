---
title: "Installed Program But It Won't Run"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-08-07
I've installed the program simple backup but it doesn't show in any lists and doesn't run when I try to run it from terminal. Here is what it's telling me in terminal:

> heaven@ubuntu:~$ simplebackup
stat: cannot stat `/home/heaven/.simplebackup.conf': No such file or directory
/usr/bin/simplebackup: line 41: /home/heaven/.simplebackup.conf: No such file or directory


sometimes ubuntu makes me feel like an idiot. *sigh*

---

### Post by kebes on 2006-08-07
Did you install the program via aptitude (or Synaptic or Adept)... or did you install it yourself from a downloaded file or somesuch?

It might be that the install didn't complete in some way.

Does the file it is looking for exist? If you go:
ls /home/heaven/.sim*

Does it find the file?

You could try uninstalling and reinstalling the program. Maybe there was an error during install you didn't notice? (If you do the install on the commandline, using "sudo aptitude install simplebackup" you might get some errors that will help understand what went wrong.)

---

### Post by arjun.shankar on 2006-08-07
The thing is this: You need to write this file yourself.

"gedit ~/.simplebackup.conf" will do fine.

To learn what to fill here type this:

"man simplebackup.conf"

---

### Post by arjun.shankar on 2006-08-07
kebes, I just installed it myself (just to see ;)). It's just a simple script. Its clear that a default conf file is not provided. Hard Luck!

---

### Post by magnoliablossom on 2006-08-07
> **arjun.shankar said:**
> The thing is this: You need to write this file yourself.

"gedit ~/.simplebackup.conf" will do fine.

To learn what to fill here type this:

"man simplebackup.conf"

ummm...obviously i don't know what i'm doing because when i do the "man simplebackup.conf" thing i just get this:

> 
NAME
       simplebackup.conf - configuration file for simplebackup(1)

DESCRIPTION
       This  file  contains  the configuration for the backups done by simple&#8208;
       backup(1).

SYNTAX
       This file is a bash(1) shell script.  It is  used  to  set  some  shell
       variables  and a shell function that are used by the backup script.  Be
       careful in what you write here: the configuration file is  sourced  and
       all commands within are executed on the beginning of a backup.

VARIABLES
       TARGETDIR
              This  is  the directory where the backup is written to.  Be sure
              to have enough free disk space here.

       WORKDIR
              This is the directory where the backup is prepared.  Disk  space
              needed here is the sum of all data to be backed up.  This direc&#8208;
              tory will be deleted on  startup,  so  don’t  point  to  anyting
              important.

       BACKUPDIRS
              These paths and their subdirectories are to be backed up.  Use :
              to separate multiple paths.

       NAME   This is the name of the backup.  It is later  prepended  with  a
              timestamp.

       LOCKFILE
              This lockfile is used to detect another running backup.  You can
              run multiple different backups in parallel  by  using  different
              lockfiles in different configurations.



Actually after looking at this more closely, I understand what it's asking for but I believe I'd rather use something else....This "Simple Backup" doesn't seem so simple to me. lol  The variables I can handle alright but the description and syntax, I have no idea what they're wanting me to put there....To me a "description" would be something on the lines of "system backup" or something but it's saying put a configuration there....

---

### Post by kebes on 2006-08-07
I've never used "simplebackup" but probably it came with a README or INSTALL file that explains how to use it the first time. By carefully reading the pages from "man simplebackup" and "man simplebackup.conf" you should be able to figure out what you need to it.

I'm guessing that in "simplebackup.conf" you must define the variables NAME, BACKUPDIR, etc. so that the simplebackup program knows what it's supposed to do. So you would edit the file and have something like:
```

TARGETDIR="/home/bob/backups/"
NAME="First Backup"
BACKUPDIR="/home/bob/data/"
WORKDIR="/home/bob/tmp/"

```

Of course that's just an example... you'll need to make it suit your needs.


Edit: I guess by "simple" they mean "minimalist" instead of "user friendly." There are many other backup solutions for linux, so you can probably find an easier one.

---

### Post by Anduu on 2006-08-07
Well when I installed it it put entries under System>Administration...i did not have to do anything such as creating the ~/.simplebackup.conf file....


**_WOOPS_** Edit....I installed "sbackup'(has a gui and everything ;))...maybe it would be more to your liking...heh

---

