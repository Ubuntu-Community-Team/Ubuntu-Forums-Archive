---
title: "Compiling lyx-svn under arch"
date: 2008-10-25
forum: Arch and derivatives
---

### Post by aquavitae on 2008-10-25
Hi

I'm trying to compile lyx from scratch - I want to tweak the source. But I'm having problems with Qt. When I run ./configure, it brings up an error about not finding the Qt libraries, which are under /opt/qt/libs.  I've manually passed the path to ./configure, but still get the error. I then tried make anyway, just in case there was a problem in ./configure and it was actually finding the libs. However, this generated a bunch of errors along the lines of "cannot find file 'QFile'".  Presumably that's a header file it can't find?  The odd thing is that the files in /opt/qt/includes are all lowercase.

Can anyone suggest what the problem might be?

---

### Post by aquavitae on 2008-10-25
I think I've sorted out - it seems that while QTDIR=/opt/qt, the actual includes and libs are in the usual place under /usr.  So I pointed configure there and its working.

---

