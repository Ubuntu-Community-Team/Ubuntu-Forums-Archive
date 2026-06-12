---
title: "OpenOffice repeat..."
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-02-18
It happened to me last time...The version of OO that is loaded by default is full of bugs and won't run properly for me.
How do I get the LATEST version..OO2?

---

### Post by taurus on 2006-02-18
What version of OpenOffice is full of bugs?  One way to use the latest version is to download it from [http://www.openoffice.org](http://www.openoffice.org) unless the version in repo is the one that you are having trouble with...

---

### Post by cilynx on 2006-02-18
Out of curiosity, what bugs are you experiencing?  I'm having problems with importing complex Word docs as well as Excel files that include charts.  If I try to import, OOo hangs.  As of now, I have to convert any MSO files that come my way to OOo on my Debian server before I can work with them on my Ubuntu desktop.

---

### Post by towsonu2003 on 2006-02-18
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

add the above line to your /etc/apt/sources.list , sudo apt-get update sudo apt-get upgrade

I didn't try it (dial up, ~100MB, 6 hours dl) but pple are using it.

---

### Post by Cesium on 2006-02-18
You could also use automatix to update OOo.

---

### Post by qwazert on 2006-02-19
[QUOTE=cilynx]Out of curiosity, what bugs are you experiencing?  I'm having problems with importing complex Word docs as well as Excel files that include charts.  If I try to import, OOo hangs.  As of now, I have to convert any MSO files that come my way to OOo on my Debian server before I can work with them on my Ubuntu desktop.[/QUOTE]

There is a BUG in the Printing portion of OO writer...constantly changes the defaults for my Printer. Upgrading to OO2 cured it last time. 
Can't remember if I did it through Synaptic or Automatix...

---

### Post by MrDez on 2006-03-08
I added the above listed apt source to my sources.list and it fixed the problem, DO NOT ATTEMPT to manually apt-get remove openoffice.org2 or it could hose your system by removing ubuntu-desktop and/or kubuntu-desktop.  I used the automatix installer about 3 weeks ago when rebuilding this box and the version it installed at the time still wasnt seeing configured printers.

Cheers.
-=Matt

---

### Post by towsonu2003 on 2006-03-08
[QUOTE=MrDez]DO NOT ATTEMPT to manually apt-get remove openoffice.org2 or it could hose your system by removing ubuntu-desktop and/or kubuntu-desktop. [/QUOTE]
Don't worry about removing ubuntu-desktop or kubuntu-desktop, if those are the only ones apt wants to remove. Those are metapackages (basically, empty) that once called for installation, will install all the elements of (k)ubuntu desktop.

so for example, I wanted to remove package ABC and apt wanted to remove (only) ubuntu-desktop. that's fine. If I later apt-get install ubuntu-desktop, apt will also install ABC... That's a way to keep everything toghether. 

PS. I recently used that link and successfully updated my OOo.. It takes loooooong (dial up)

---

