---
title: "file integrity, with md5 ?"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by noteforself on 2005-10-18
hi everyone,

i am switching over from windows xp.  on windows, i used a program called wxchecksums, located at [http://sourceforge.net/projects/wxchecksums/](http://sourceforge.net/projects/wxchecksums/)

basically, when i backed up my data, i made a folder with everything i wanted to save, and included in it is an md5 file.  the folder compressed with 7zip and then burned to a cd.

when i retrieve the data from the cd, i verify the integrity of the data with the md5 file.

my question is, is there an easy program that creates and verifies md5 and has a graphical user interface for ubuntu?

much appreciation for helping a switcher.

---

### Post by BoyOfDestiny on 2005-10-18
[QUOTE=noteforself]hi everyone,

i am switching over from windows xp.  on windows, i used a program called wxchecksums, located at [http://sourceforge.net/projects/wxchecksums/](http://sourceforge.net/projects/wxchecksums/)

basically, when i backed up my data, i made a folder with everything i wanted to save, and included in it is an md5 file.  the folder compressed with 7zip and then burned to a cd.

when i retrieve the data from the cd, i verify the integrity of the data with the md5 file.

my question is, is there an easy program that creates and verifies md5 and has a graphical user interface for ubuntu?

much appreciation for helping a switcher.[/QUOTE]

I use it too. If you notice in the link you posted...

wxChecksums is a program which calculates and verifies checksums. wxChecksums is able to read and write files in SFV and MD5 format. It is available for Windows 9x/ME/2000/XP and Linux.

    * Development Status: 5 - Production/Stable
    * Intended Audience: End Users/Desktop
    * License: GNU General Public License (GPL)
    * Operating System: All 32-bit MS Windows (95/98/NT/2000/XP), All POSIX (Linux/BSD/UNIX-like OSes), **Linux**
    * Programming Language: C++
    * Topic: Archiving
    * Translations: English, French
    * User Interface: **Gnome, KDE,** Win32 (MS Windows)

---

### Post by noteforself on 2005-10-18
[QUOTE=BoyOfDestiny]I use it too. If you notice in the link you posted...

wxChecksums is a program which calculates and verifies checksums. wxChecksums is able to read and write files in SFV and MD5 format. It is available for Windows 9x/ME/2000/XP and Linux.

    * Development Status: 5 - Production/Stable
    * Intended Audience: End Users/Desktop
    * License: GNU General Public License (GPL)
    * Operating System: All 32-bit MS Windows (95/98/NT/2000/XP), All POSIX (Linux/BSD/UNIX-like OSes), **Linux**
    * Programming Language: C++
    * Topic: Archiving
    * Translations: English, French
    * User Interface: **Gnome, KDE,** Win32 (MS Windows)[/QUOTE]


!!  i didn't think of checking the breezy repositories for that specific program... but did a search for md5 instead and came across something called cfv.  thanks, i'm going to look into it now.

---

### Post by noteforself on 2005-10-18
[QUOTE=noteforself]!!  i didn't think of checking the breezy repositories for that specific program... but did a search for md5 instead and came across something called cfv.  thanks, i'm going to look into it now.[/QUOTE]


i couldn't find it in the ubuntu repositories.  (note: i'm using AMD 64 version of ubuntu.  the source code is available for it but i am not a programmer at all.)

is there a similar program that does the same thing for the ubuntu AMD 64 platform?

thanks in advance.

---

### Post by lotusleaf on 2005-10-18
[QUOTE=noteforself]my question is, is there an easy program that creates and verifies md5 and has a graphical user interface for ubuntu?
[/QUOTE]

The latest beta and cvs version(s) of **Krusader** now offer support for the most excellent **md5deep** program. Or, you could just use md5deep from the command line which is simple and easy to generate *recursive* md5 and/or other checksums supported by md5deep. Links to both programs in my sig below or google them.

---

