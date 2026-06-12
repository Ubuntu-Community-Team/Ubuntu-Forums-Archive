---
title: "Problem installing wine"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-17
I tried installing wine in my ubuntu using this guide:
[http://ubuntuforums.org/showthread.php?t=149585&highlight=installing+program+wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=installing+program+wine)
I'm stuck @
 wine "/home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
I know my username & I can't seemed to find .wine directory I can't seem to see it @ home folder in it.
thanks. I'm so use to windows & I'm really confuse!!!

---

### Post by x64Jimbo on 2006-07-17
When a directory has a dot in front of its name, it's invisible unless you ls -a
You can still cd into it though. Don't worry. :)
I'll tell you that it shouldn't be in ~/.wine/c/Program Files/...etc
It should be in ~/.wine/drive_c/Program Files/...etc.
Give that a shot.

---

### Post by kris2pe on 2006-07-17
How do I search 4 it? coz I wanna where its been place. So that I have sense of how to put other programs wine! Thanks
So how should the entire code look like?
wine "/home/tope/~/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
this?

---

### Post by qamelian on 2006-07-17
> **kris2pe said:**
> How do I search 4 it? coz I wanna where its been place. So that I have sense of how to put other programs wine! Thanks
So how should the entire code look like?
wine "/home/tope/~/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
this?

The ~ character represents your home directory so you don't need to include "/home/tope/". Using "~/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE" should be sufficient.

---

### Post by kris2pe on 2006-07-17
its weird coz he gave me all this instruction & it doesn't work 
I don't think i've seen a .wine directory on my home folder though!!!
tope@tope-desktop:~$ wine: "~/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
bash: wine:: command not found

---

### Post by echo $USER on 2006-07-17
> **kris2pe said:**
> its weird coz he gave me all this instruction & it doesn't work 
I don't think i've seen a .wine directory on my home folder though!!!
tope@tope-desktop:~$ wine: "~/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
bash: wine:: command not found

You have to escape the white space with \ between Program and files, Internet and Explorer like this...

> ~/.wine/drive_c/Program\ Files/Internet\ Explorer/IEXPLORE.EXE

and its drive_c not just c

just do this...

> cd ~/.wine/drive_c/Program\ Files/Internet\ Explorer

then run 
> 
wine IEXPLORE.EXE

---

### Post by kris2pe on 2006-07-17
I tried using winefile its much easier!!!
How do I install firefox in wine? Coz I think its more stable to use!

---

### Post by x64Jimbo on 2006-07-18
Firefox has a Linux version. You should really use native apps whenever you can, since Wine is still in alpha. You can install it by going to your package manager and searching for firefox. 
You may also run a version of Windows Firefox on your system if you require Flash Player 9, since Adobe has not released version 9 for Linux yet (we're still using version 7 if you can believe it.)  I have Windows Firefox set up separately from my normal Firefox so that if I find a site that needs the latest version, I can still view the page.

---

