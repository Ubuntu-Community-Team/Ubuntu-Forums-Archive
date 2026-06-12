---
title: "Clamav got missing"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-03-27
I ran sudo apt-get install clamav-data
To update definitions because i will be passing on files to windows users, after the terminal had finished, virus scanner is no longer listed in applications. Even though i have a copy of clam still running so i know its still on the computer. How can i get clamav back?

---

### Post by wolfen69 on 2008-03-27
did you try system>preferences>main menu? also, did you ever see the gui? that may need to be installed.

---

### Post by bumanie on 2008-03-27
I assume you are wanting a front-end to clam av.
> wget [http://puzzle.dl.sourceforge.net/sourceforge/clamtk/clamtk_3.05-1_all.deb](http://puzzle.dl.sourceforge.net/sourceforge/clamtk/clamtk_3.05-1_all.deb)
> sudo dpkg -i clamtk_3.05-1_all.deb
I think this will install what you are looking for.

---

### Post by Falc7 on 2008-03-27
Sorry for not making myself more clear. Yep before i had the GUI front end. And i could access it through applications -> accessories
A few minutes ago i ran sudo apt-get install clamav-data
Now clam av is gone from applications, however i still have a copy of the gui running on the desktop. But if i close it, with it now gone from applications, i won't know how to start another one.

I've just tried system-> main menu,
however virus scanner is not present there

Its strange, when i go on add/remove programs clam is listed as not being present on my system, and when i try to install from there, it says existing software conflicts with it.

wer@wer-laptop:~$ sudo dpkg -i clamtk_3.05-1_all.deb
dpkg: error processing clamtk_3.05-1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 clamtk_3.05-1_all.deb

---

### Post by Malta paul on 2008-03-27
Hi when you install 'clamav-data' Clamtk will be deleted. Thats why you can't find it under accessories.
To get it back go to the terminal 'Sudo apt-get install clamtk' and your graphics display will be back. :)

---

### Post by Falc7 on 2008-03-27
Ok thanks, when putting that in the terminal it says:
The following packages will be REMOVED
  clamav-data

What is the best way to update clam then if not by installing clamav-data?

---

### Post by Malta paul on 2008-03-27
HI, I may be saying rubbish but I think the virus signature for clamav is updated during the boot up sequence.

---

### Post by Falc7 on 2008-03-28
that would be good, could anyone confirm or deny?

---

### Post by Falc7 on 2008-03-29
anyone know a way to check if this is the case? Perhaps by checking a list of startup programs or something?

---

### Post by gohsthb on 2008-03-30
I've always used 'freshclam' to update the definitions

---

### Post by kitterma on 2008-04-23
clamtk depends on freshclam (which downloads updates over the network).  Freshclam and clamav-data conflict.  If you have a network connection even some of the time you want freshclam so you can get new updates to the virus definitions automatically.

---

