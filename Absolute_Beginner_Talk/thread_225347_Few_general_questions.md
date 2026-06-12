---
title: "Few general questions"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by ironfistchamp on 2006-07-29
Hey all some n00blike questions here. Suprised I haven't asked before.

1) When in a terminal (Ctrl+Alt+F(x)) ls lists too much. The top items got knocked off the screen in some places. Is there an option I can use to just fill a screen and hit a key to fill the next?

2) When a company decideds to port an app what do they have to do? Do they try and compile current source code on a *nix box and see what happens?

3) How does the community actually give back with regards to bugs. Do we acutally fix them and send in our patchs or just report?

I think that is all for now but I am sure I will think of more.

Thanks

Ironfistchamp

---

### Post by moma on 2006-07-29
1)  Use **more** or **less**
$ ls  | less 
$ dir -l /usr/bin | more 

Press spacebar for next page. q to guit.
----------------------------------

2) Yes that's a good idea, but one should also apply **coding standards** when porting applications to *nix/linux.  I especially think that Linux-apps should conform the LSB (Linux Standard Base) spesification.

[http://www.freestandards.org/spec/]("http://www.freestandards.org/spec/")

Developing LSB based applications
[http://www-128.ibm.com/developerworks/linux/library/l-lsb.html]("http://www-128.ibm.com/developerworks/linux/library/l-lsb.html")

LSB Books
[http://www.freestandards.org/spec/booksets/]("http://www.freestandards.org/spec/booksets/")

And if the application has a GUI (Graphical User Interface) component, then it must comply with the Freedesktop.org's standards.

[http://freedesktop.org/wiki/Standards]("http://freedesktop.org/wiki/Standards")

Plus either GNOME's or KDE's HIG (Human Interface Guidelines).

KDE's HIG
[http://wiki.kde.org/tiki-index.php?page=KDE%20HIG]("http://wiki.kde.org/tiki-index.php?page=KDE%20HIG")

GNOME's HIG
[http://developer.gnome.org/projects/gup/hig/](http://developer.gnome.org/projects/gup/hig/)

These [FAQ pages...]("http://home.online.no/%7Eosmoma/opportunities.html") may help when porting to Linux.

Software installation (deployment) should be based on GNU Autotools.
Autotools comprises of Automake, Autoconf and Libtool tools.
[http://sources.redhat.com/autobook/]("http://sources.redhat.com/autobook/")
Software (source code) configured using Autotools is very portable within all known Unix/Linux plattforms.
----------------------------------

3) Bug-reports are always welcomed by the developers.

---

### Post by ironfistchamp on 2006-07-29
Hehe lots for me to read thanks. :D

---

