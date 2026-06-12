---
title: "DELL AIO A920 Printer"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by xdwmx on 2007-06-18
Hey guys.

I just installed Ubuntu 7.04 earlier today and I'm liking it, a lot. My internet, video and sound are all working fine but my DELL (Lexmark) AIO A920 printer isn't working. Using Ubuntu's printer detection tool, It recognised my printer but it never had any available drivers. I have searched Google which returned numerous results but I'm lost and don't really know how to install my printer. I don't know where to get the drivers or how to install them.

Any help appreciated.

---

### Post by Austin_KW on 2007-06-18
It will not work on linux.

---

### Post by xdwmx on 2007-06-18
Yes it will.

I have read through many threads where people have managed to get it to print, but not to scan. I'm just trying to follow them in their footsteps.

---

### Post by Austin_KW on 2007-06-18
I presume this is the fabled lexmark z600 driver,

try this ( but I had no joy with lexmark/dell AIOs)
[http://www.finebushpeople.net/index.php?option=content&task=view&id=65&Itemid=98/](http://www.finebushpeople.net/index.php?option=content&task=view&id=65&Itemid=98/)

---

### Post by xdwmx on 2007-06-18
I followed to steps in the link you gave me but I'm stuck on the step;

"To install to a debian system (or Ubuntu or Knoppix) you need to convert these two files to the .deb equivalent. The program to use is called "alien" and you run it as follows:
$ alien z600cups-1.0-1.i386.rpm
$ alien z600llpddk-2.0-1.i386.rpm"

I have the two above .rpm files in my 'home\temp_lex' folder. But when I run the alien z600cups-1.0-1.i386.rpm commands I get the message "File "z600cups-1.0-1.i386.rpm" not found."

It finds the files when I copy them into my home folder, but I get the error "Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts." Though it creates the .deb files.

When I try to install the drivers in the next step I get the message "dpkg: error processing z600llpddk-2.0-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 z600llpddk-2.0-1.i386.deb".

I need help.

---

