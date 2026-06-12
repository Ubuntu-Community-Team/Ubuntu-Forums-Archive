---
title: "So, installing a program..."
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Eltern on 2006-02-02
So, I've been dual-booting Kubuntu and XP for awhile, and want to make a more solid transition to Linux, so I'm trying to get some of my essential Windows programs over on Linux. Which means learning how to actually install programs, which I've somehow avoided doing :p 

The program in question is Petite Chez Scheme, for a computer science class. I downloaded the RPM here: [http://www.scheme.com/csv7.0a/](http://www.scheme.com/csv7.0a/)
I converted this to a .deb with alien. Now I've unpackaged the .deb -twice-, I think. Once in the GUI with Adept, and once in the terminal with sudo dpkg. Now, I didn't get any messages about dependencies or anything so....where is it?

No, seriously. Where do I go to find this program I just installed? :D I haven't the faintest idea where to look, and my initial searches brought up nothing.

Thanks!

---

### Post by Sutekh on 2006-02-02
You should try simply typing the name of the program in a terminal window or using Alt+F2
```

petite
```

---

### Post by Stealth on 2006-02-02
Ok, well, some programs don't create menu items. To figure out what program to launch after an install like that you can try this:

Open up Synaptic, and search for the program you installed. If you see the package in the list (probably has some stuff about being converted by alien in the description) then right click on it and go to properties. Then go to te installed files tab and you will probably find a line like /usr/bin/prog where prog should be an abbreviated or cut down name of the program you're looking for. That usually will help! :D

---

### Post by Eltern on 2006-02-02
Just using alt F2 didn't work :-\ 

Does Synaptic come in KDE? Because, again, it's not in the menu items, so I can't find it. I did look at the package info from the Kubuntu Package Menu, and I got this:

 new debian package, version 2.0.
 size 722750 bytes: control archive= 1487 bytes.
     738 bytes,    17 lines      control              
    2000 bytes,    31 lines      md5sums              
 Package: petitechezscheme
 Version: 7.0a-2
 Section: alien
 Priority: extra
 Architecture: i386
 Depends: libc6 (>= 2.3.4-1), libncurses5 (>= 5.4-5)
 Installed-Size: 1024
 Maintainer: root <root@localhost.localdomain>
 Description: Petite Chez Scheme: An implementation of Scheme
  Petite Chez Scheme is a freely distributable interpreted version of Chez
  Scheme, a high-performance implementation of ANSI Scheme with numerous
  extensions.  Petite Chez Scheme may be used as a run-time environment
  for compiled Chez Scheme applications or as a stand-alone Scheme system.
  With the exception that the compiler is not present, Petite Chez Scheme
  is completely compatible with Chez Scheme.
  .
  (Converted from a rpm package by alien version 8.53.)
 
Status: 
install ok installed
----
Package contents:
 
drwxr-xr-x root/root         0 2006-02-02 20:11:10 ./
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/share/
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/share/doc/
drwxr-xr-x root/root         0 2006-02-02 20:11:10 ./usr/share/doc/petitechezscheme/
-rw-r--r-- root/root      1225 2006-02-02 20:11:09 ./usr/share/doc/petitechezscheme/copyright
-rw-r--r-- root/root       192 2006-02-02 20:11:09 ./usr/share/doc/petitechezscheme/changelog.Debian.gz
drwxr-xr-x root/root         0 2006-02-02 20:11:10 ./usr/share/doc/PetiteChezScheme-7.0a/
-r--r--r-- root/root      2347 1999-03-04 13:57:16 ./usr/share/doc/PetiteChezScheme-7.0a/petite.lic.gz
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/share/man/
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/share/man/man1/
-r--r--r-- root/root      5711 2005-12-04 20:40:30 ./usr/share/man/man1/petite.1.gz
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/bin/
-r-x--x--x root/root    198527 2005-12-04 20:40:30 ./usr/bin/petite
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/lib/
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/lib/csv7.0a/
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/lib/csv7.0a/i3le/
-r--r--r-- root/root    588786 2005-11-19 15:14:34 ./usr/lib/csv7.0a/i3le/petite.boot
-r--r--r-- root/root      5493 2005-09-08 15:09:28 ./usr/lib/csv7.0a/i3le/scheme.h
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/lib/csv7.0a/lib/
-r--r--r-- root/root      1291 2005-05-12 12:47:41 ./usr/lib/csv7.0a/lib/Makefile
-r--r--r-- root/root      7591 1999-11-08 16:54:08 ./usr/lib/csv7.0a/lib/compat.ss
-r--r--r-- root/root      2210 1998-09-18 19:31:54 ./usr/lib/csv7.0a/lib/csocket.c
-r--r--r-- root/root      4458 1998-09-18 15:31:48 ./usr/lib/csv7.0a/lib/def.ss
-r--r--r-- root/root     19292 1990-06-27 14:28:06 ./usr/lib/csv7.0a/lib/edit.ss
-r--r--r-- root/root       289 1989-01-30 09:04:55 ./usr/lib/csv7.0a/lib/fact.ss
-r--r--r-- root/root       458 1989-01-30 09:04:55 ./usr/lib/csv7.0a/lib/fatfib.ss
-r--r--r-- root/root      1380 1996-10-11 09:58:27 ./usr/lib/csv7.0a/lib/fft.ss
-r--r--r-- root/root       187 1989-01-30 09:04:55 ./usr/lib/csv7.0a/lib/fib.ss
-r--r--r-- root/root      6020 1997-06-18 14:20:49 ./usr/lib/csv7.0a/lib/foreign.ss
-r--r--r-- root/root      3732 1996-10-11 10:10:35 ./usr/lib/csv7.0a/lib/freq.ss
-r--r--r-- root/root      3091 1996-10-11 09:56:22 ./usr/lib/csv7.0a/lib/interpret.ss
-r--r--r-- root/root     23064 1991-02-27 11:26:25 ./usr/lib/csv7.0a/lib/m4.ss
-r--r--r-- root/root      2773 1996-10-11 09:39:53 ./usr/lib/csv7.0a/lib/macro.ss
-r--r--r-- root/root      3456 1996-10-11 09:57:33 ./usr/lib/csv7.0a/lib/matrix.ss
-r--r--r-- root/root      1280 1996-10-11 09:51:57 ./usr/lib/csv7.0a/lib/object.ss
-r--r--r-- root/root       280 1989-01-30 09:04:55 ./usr/lib/csv7.0a/lib/power.ss
-r--r--r-- root/root      1823 1990-07-23 17:08:07 ./usr/lib/csv7.0a/lib/queue.ss
-r--r--r-- root/root      3052 1996-05-01 13:18:16 ./usr/lib/csv7.0a/lib/rabbit.ss
-r--r--r-- root/root     10510 2005-05-12 12:42:25 ./usr/lib/csv7.0a/lib/rsa.ss
-r--r--r-- root/root      1123 1996-10-11 09:49:16 ./usr/lib/csv7.0a/lib/scons.ss
-r--r--r-- root/root      1016 1996-10-11 09:52:10 ./usr/lib/csv7.0a/lib/setof.ss
-r--r--r-- root/root     11231 2005-11-18 13:25:44 ./usr/lib/csv7.0a/lib/socket.ss
-r--r--r-- root/root      2367 1996-10-11 09:52:07 ./usr/lib/csv7.0a/lib/unify.ss

I did find some .gz files in usr/share/doc/petitechezscheme, but nothing useful. Thoughts?

---

### Post by Sutekh on 2006-02-02
[QUOTE=Eltern]Just using alt F2 didn't work :-\ 
[/QUOTE]
How about from Konsole?
[QUOTE=Eltern]

...
drwxr-xr-x root/root         0 2006-02-02 20:11:09 ./usr/bin/
-r-x--x--x root/root    198527 2005-12-04 20:40:30 **./usr/bin/petite**
...

Thoughts?[/QUOTE]
This is the executable, **petite** should be the command to run it.

---

### Post by Eltern on 2006-02-02
It is indeed there, and it's an unknown file type which I don't have permission to read. I'm assuming this is a problem with the program, then, and not my own ignorance?

When using Konsole:

jeff@ubuntu:~$ sudo /usr/bin/petite
Password:
Petite Chez Scheme Version 7.0a
Copyright (c) 1985-2005 Cadence Research Systems

> 

And that's it. Am I missing a step somewhere?

---

### Post by Sutekh on 2006-02-02
The entry
```

-r-x--x--x root/root 198527 2005-12-04 20:40:30 ./usr/bin/petite

```
displays the properties for the file /usr/bin/petite.  You can replicate this entry by using the code
```

ls -l /usr/bin/petite
```

Ok, getting back to the entry

The first part of this line is made up of ten dashes (-), the first is a - meaning its a file, a d would mean its a directory.  The next nine represent the permissions of the file.

r - means read permissions
w - mean write permissions
x - means execute (run) permissions

The first group of three apply to the owner, which in this case is **root**.  This means the user root 'own's this file.

The second group apply to the group owner, which is **root**.  This means users who are in the group root 'own' this file.

The last group of three apply to anyone else, who is not the owner or in the owning group.

Ok, you can change the ownership and permissions of the file using 
```

sudo chown jeff:jeff /usr/bin/petite

```
This changes the owner of /usr/bin/petite to **jeff** and the group ownership belongs to **jeff**.  You may wish to change and can do so simply by changing the **<username>:<groupname>** part.
```

sudo chmod 777 /usr/bin/petite

```
This changes the read, write and execute permissions to yes for the owner, group and everyone else.  You can change this further if you wish to allow restricted access.

So after all this I would then expect to see
```

-rwxrwxrwx jeff/jeff 198527 2005-12-04 20:40:30 ./usr/bin/petite

```

Then you should be able to run it, using **petite**

The fact that it was initially owned by root, means to me, that you isntalled the program using sudo?  If its not a special program that is gonna do system wide changes, then I wouldn't install using sudo.  That way your user will own the files of the installation.

---

### Post by Sutekh on 2006-02-02
After writing all that I noticed that you already have execute permissions for the file /usr/bin/petite.  You really ought to be able to run it straight from Konsole.  Just use **petite** not /usr/bin/petite.  Perhaps try **./petite** as well.

---

### Post by Eltern on 2006-02-03
Well, I've figured out a thing or two. When I presented this:

jeff@ubuntu:~$ petite
Petite Chez Scheme Version 7.0a
Copyright (c) 1985-2005 Cadence Research Systems

>

I had actually launched Petite, inside the console, and hadn't realized it. This basically just opened a repl of Scheme for me. Wee! Getting close!

However, I'm used to, and in some cases required to, using the Scheme Widget Library (SWL), which is GUI interface for Petite Chez Scheme. I hadn't realized that the SWL only comes automatically with the Windows version of Petite, so I went to the same site and downloaded the .rpm of the SWL. Used alien to convert to .deb. Installed the package. 

And now I'm at the same problem I was at before, with a different program :) Maybe some more general principles of how to find the location of a newly installed program would be more useful to me, since I evidently didn't learn that skill from my attempts with Petite.

I can post up all the info for the new package, but what can you guys tell me in what I should be looking for, so I know how to do it myself?

---

### Post by Eltern on 2006-02-05
::bump::

---

