---
title: "[SOLVED] pico config problem in solaris"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by rbprogrammer on 2008-01-22
ok so in the class i am taking, the professor wants us to ssh into a sun system and do our homework and whatnot on there through the ssh.  all the homework is done with a simple text editor.    there are a few installed on the system, but since nano is not installed i figured pico is the next best one that i like.  my question is, when i hit the tab key, a tab character is inserted (obviously).  but when i want is to have 4 whitespaces inserted.  i know how to do it on my home ubuntu box with nano, but i cant seem to find the pico config file on the solaris system.  does anyone know how to change this??  or where the config file is saved??

---

### Post by jfinkels on 2008-01-24
You will probably have to use a "~/.nanorc" file (or "~/.picorc" I suppose if the system is so old that it doesn't even have nano, an updated pico). Type "man nano" and "man nanorc" for more info on configuration files.

---

### Post by rbprogrammer on 2008-01-24
this is what i got from the list command:
```

% ls -la
total 200
drwx--x--x   7 mwd5025  ucse        4096 Jan 22 16:46 ./
drwxr-xr-x 392 root     root       12288 Jan 16 14:23 ../
-rw-r--r--   1 mwd5025  ucse        2574 Apr  4  2005 .Xresources
-rwxr-xr-x   1 mwd5025  ucse        3454 Apr  4  2005 .Xsession*
-rw-r--r--   1 mwd5025  ucse        2707 Apr 28  2005 .cshrc
drwx------   3 mwd5025  ucse        4096 Aug 10 15:20 .dt/
drwx------   3 mwd5025  ucse        4096 Jan 22 16:29 .emacs.d/
-rw-r--r--   1 mwd5025  ucse           0 Mar  1  2005 .fvwm2desk
-rw-r--r--   1 mwd5025  ucse       12271 Mar  1  2005 .fvwm2rc
drwx------   2 mwd5025  ucse        4096 Aug 10 15:20 .hold/
-rwxr-xr-x   1 mwd5025  ucse         219 Mar  1  2005 .login*
-rwxr-xr-x   1 mwd5025  ucse          75 Mar  1  2005 .logout*
-rw-r--r--   1 mwd5025  ucse        3728 Apr 28  2005 .profile
drwx------   3 mwd5025  ucse        4096 Jan 22 11:14 .sunstudio/
-rw-r--r--   1 mwd5025  ucse        5884 Mar  1  2005 .twmrc
-rw-------   1 mwd5025  ucse        1315 Jan 22 16:46 .viminfo
lrwxrwxrwx   1 mwd5025  ucse           9 Aug 22 17:34 .xinitrc -> .Xsession*
lrwxrwxrwx   1 mwd5025  ucse           9 Aug 22 17:34 .xsession -> .Xsession*
drwx------   3 mwd5025  ucse        4096 Jan 22 10:50 CMPSC311/

```
or if i do it recursively, i get:
```

% ls -laR
.:
total 200
drwx--x--x   7 mwd5025  ucse        4096 Jan 22 16:46 ./
drwxr-xr-x 392 root     root       12288 Jan 16 14:23 ../
-rw-r--r--   1 mwd5025  ucse        2574 Apr  4  2005 .Xresources
-rwxr-xr-x   1 mwd5025  ucse        3454 Apr  4  2005 .Xsession*
-rw-r--r--   1 mwd5025  ucse        2707 Apr 28  2005 .cshrc
drwx------   3 mwd5025  ucse        4096 Aug 10 15:20 .dt/
drwx------   3 mwd5025  ucse        4096 Jan 22 16:29 .emacs.d/
-rw-r--r--   1 mwd5025  ucse           0 Mar  1  2005 .fvwm2desk
-rw-r--r--   1 mwd5025  ucse       12271 Mar  1  2005 .fvwm2rc
drwx------   2 mwd5025  ucse        4096 Aug 10 15:20 .hold/
-rwxr-xr-x   1 mwd5025  ucse         219 Mar  1  2005 .login*
-rwxr-xr-x   1 mwd5025  ucse          75 Mar  1  2005 .logout*
-rw-r--r--   1 mwd5025  ucse        3728 Apr 28  2005 .profile
drwx------   3 mwd5025  ucse        4096 Jan 22 11:14 .sunstudio/
-rw-r--r--   1 mwd5025  ucse        5884 Mar  1  2005 .twmrc
-rw-------   1 mwd5025  ucse        1315 Jan 22 16:46 .viminfo
lrwxrwxrwx   1 mwd5025  ucse           9 Aug 22 17:34 .xinitrc -> .Xsession*
lrwxrwxrwx   1 mwd5025  ucse           9 Aug 22 17:34 .xsession -> .Xsession*
drwx------   3 mwd5025  ucse        4096 Jan 22 10:50 CMPSC311/

./.dt:
total 24
drwx------   3 mwd5025  ucse        4096 Aug 10 15:20 ./
drwx--x--x   7 mwd5025  ucse        4096 Jan 22 16:46 ../
drwx------   2 mwd5025  ucse        4096 Aug 10 15:20 sessions/

./.dt/sessions:
total 24
drwx------   2 mwd5025  ucse        4096 Aug 10 15:20 ./
drwx------   3 mwd5025  ucse        4096 Aug 10 15:20 ../
-rw-r--r--   1 mwd5025  ucse          29 Apr  4  2005 lastsession
lrwxrwxrwx   1 mwd5025  ucse          15 Aug 22 17:34 sessionetc -> ../../.Xsession*

./.emacs.d:
total 40
drwx------   3 mwd5025  ucse        4096 Jan 22 16:29 ./
drwx--x--x   7 mwd5025  ucse        4096 Jan 22 16:46 ../
drwx------   2 mwd5025  ucse        4096 Jan 22 16:29 auto-save-list/

./.emacs.d/auto-save-list:
total 40
drwx------   2 mwd5025  ucse        4096 Jan 22 16:29 ./
drwx------   3 mwd5025  ucse        4096 Jan 22 16:29 ../
-rw-------   1 mwd5025  ucse           0 Jan 22 16:29 .saves-25150-melmak.cse.psu.edu~

./.hold:
total 16
drwx------   2 mwd5025  ucse        4096 Aug 10 15:20 ./
drwx--x--x   7 mwd5025  ucse        4096 Jan 22 16:46 ../

./.sunstudio:
total 40
drwx------   3 mwd5025  ucse        4096 Jan 22 11:14 ./
drwx--x--x   7 mwd5025  ucse        4096 Jan 22 16:46 ../
drwx------   2 mwd5025  ucse        4096 Jan 22 17:25 user_info/

./.sunstudio/user_info:
total 120
drwx------   2 mwd5025  ucse        4096 Jan 22 17:25 ./
drwx------   3 mwd5025  ucse        4096 Jan 22 11:14 ../
-rw-------   1 mwd5025  ucse         128 Jan 22 17:25 activity_sun_studio_11_solaris-SPARC
-rw-------   1 mwd5025  ucse       29412 Jan 22 17:25 latest_updates.html

./CMPSC311:
total 40
drwx------   3 mwd5025  ucse        4096 Jan 22 10:50 ./
drwx--x--x   7 mwd5025  ucse        4096 Jan 22 16:46 ../
drwx------   3 mwd5025  ucse        4096 Jan 22 16:25 project1/

./CMPSC311/project1:
total 152
drwx------   3 mwd5025  ucse        4096 Jan 22 16:25 ./
drwx------   3 mwd5025  ucse        4096 Jan 22 10:50 ../
-rw-------   1 mwd5025  ucse         898 Jan 21 12:44 Makefile
-rw-------   1 mwd5025  ucse         126 Jan 19 09:05 dos-style.c
-rwx------   1 mwd5025  ucse        7944 Jan 22 11:14 pr1*
-rw-------   1 mwd5025  ucse         637 Jan 16 12:34 pr1.2.c
-rw-------   1 mwd5025  ucse        2637 Jan 23 16:57 pr1.3.c
drwx------   2 mwd5025  ucse        4096 Jan 22 17:37 testdata/
-rw-------   1 mwd5025  ucse         118 Jan 19 09:05 unix-style.c

./CMPSC311/project1/testdata:
total 184
drwx------   2 mwd5025  ucse        4096 Jan 22 17:37 ./
drwx------   3 mwd5025  ucse        4096 Jan 22 16:25 ../
-rwx------   1 mwd5025  ucse        6112 Jan 22 17:36 a.out*
-rw-------   1 mwd5025  ucse          16 Jan 18 11:06 mixed123
-rw-------   1 mwd5025  ucse          77 Jan 22 17:36 testdata.c
-rw-------   1 mwd5025  ucse           4 Jan 22 17:37 testdos0
-rw-------   1 mwd5025  ucse           3 Jan 22 17:35 testunix0
-rw-------   1 mwd5025  ucse          64 Jan 22 17:33 testunix1
-rw-------   1 mwd5025  ucse          14 Jan 17 00:08 vi123
-rw-------   1 mwd5025  ucse          17 Jan 16 23:56 word123.txt
-rw-------   1 mwd5025  ucse          15 Jan 16 23:52 wordpad123.txt

```
clearly there is no user defined pico config file in my home directory, and i looked at "man pico" but got nothing on the configuration file.... hrmmmm :confused:

---

### Post by jfinkels on 2008-01-24
In some cases, if a local configuration file doesn't already exist, you may have to create it yourself.

Do you have nano, which is a GNU 'clone' of pico redistributed under the GPL? If so, have you looked at "man nanorc"? As for actual documentation for pico...good luck. You may need to scour the internet and find some sort of manual. It's been long forgotten, methinks.

Also, have you considered emacs or vi? The best way to learn is by using them, and they will help you a lot if you continue in programming, I can attest to that.

---

### Post by rbprogrammer on 2008-01-24
> **jfinkels said:**
> 
Do you have nano, which is a GNU 'clone' of pico redistributed under the GPL? If so, have you looked at "man nanorc"? As for actual documentation for pico...good luck. You may need to scour the internet and find some sort of manual. It's been long forgotten, methinks.

Also, have you considered emacs or vi? The best way to learn is by using them, and they will help you a lot if you continue in programming, I can attest to that.


lol, nope no [FONT="Courier New"]man nano[/FONT] or [FONT="Courier New"]man nanorc[/FONT] entry.  all that is installed on the system is pico and vi (or vim, whichever).  maybe emacs, but i really prefer nano (or pico in this case).  to me its much more intuitive and user friendly.  my professor uses vi and encourages us to use it, but quite frankly it drives me nuts.  as for pico documentation, you're right, there is virtually nothing, i can only find nano docs.

oh by the way, if it helps me to post this, i guess this is the version of solaris that the university is using:
```
SunOS Release 5.10 Version Generic_118833-36 [UNIX(R) System V Release 4.0]
```

---

### Post by rbprogrammer on 2008-02-21
the only way i got this to work was just forget pico and manually install nano, which went something like this:
```

ssh onto-machine
cd
wget http://www.nano-editor.org/dist/v2.0/nano-2.0.7.tar.gz
tar -xf nano-2.0.7.tar.gz
cd nano-2.0.7
./configure
make
make check
make install

```
then i could add the hidden home files that controlled the way nano looked and acted.  for instance i hate the "jumping" when you scroll.  i like it when the scroll is smooth.

---

### Post by jfinkels on 2008-02-21
Great! I'm glad you were able to solve this problem.

---

