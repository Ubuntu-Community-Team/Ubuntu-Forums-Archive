---
title: "Trying To Install Windows Codecs for Totem Player"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Avenue on 2006-09-27
Hello All, 

I am very new to Linux and trying to install the codecs for Windows Media files to be used with Totem player. After going to the RestrictedFormats page, I copied and pasted the install commands and ran them. After this is run or installed (at this point i'm not sure what these commands do, does this mean they are just downloaded??) I get this error:

[B]chad@Avenue:~$ sudo dpkg -i w32codecs_20060611-1plf1_i386.de
Password:
dpkg: error processing w32codecs_20060611-1plf1_i386.de (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
w32codecs_20060611-1plf1_i386.de[/B]

Unfortunately I have no idea what the above means. What do I do next?

Thanks for the help!!

---

### Post by Buffalo Soldier on 2006-09-27
> **Avenue said:**
> Hello All, 

I am very new to Linux and trying to install the codecs for Windows Media files to be used with Totem player. After going to the RestrictedFormats page, I copied and pasted the install commands and ran them. After this is run or installed (at this point i'm not sure what these commands do, does this mean they are just downloaded??) I get this error:

[B]chad@Avenue:~$ sudo dpkg -i w32codecs_20060611-1plf1_i386.de
Password:
dpkg: error processing w32codecs_20060611-1plf1_i386.de (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
w32codecs_20060611-1plf1_i386.de[/B]

Unfortunately I have no idea what the above means. What do I do next?

Thanks for the help!!

Perhaps you missed a letter/character?

sudo dpkg -i w32codecs_20060611-1plf1_i386.de**[color=red]b[/color]**

---

### Post by redester on 2006-10-04
I copied and pasted and also got;


sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
dpkg: error processing w32codecs_20060611-1plf1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-1plf1_i386.deb

Totem in its present state is useless here.

Ray

---

### Post by Aberrix on 2006-10-04
try automatix, super easy and worked perfect for me.

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by PPAAUULL on 2006-10-04
Ya Automatix is awsome. either that or easy Ubuntu. Both are good programs for doing just that!

---

