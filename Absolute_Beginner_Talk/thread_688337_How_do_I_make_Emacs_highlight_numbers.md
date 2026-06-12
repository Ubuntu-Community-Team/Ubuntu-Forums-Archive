---
title: "How do I make Emacs highlight numbers?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2008-02-05
When coding in Emacs, is there a way to make numbers show up differently (different color, etc.)?  For example, if I code 

a = 2.0 

or 

b = 5 + exp(3.0)

I would like to have the 2.0 or 5  and 3.0 show up in a color different from the rest of the syntax highlighting.  I've found ways to make most other parts of code show up differently, but no luck so far on numbers like that.  What should I add to my .emacs file to make this happen?  Thanks.

---

### Post by Cypher on 2008-02-05
[This file]("http://www.mail-archive.com/jde@sunsite.auc.dk/msg04347.html") describes the things you can do to highlight numbers, comments and other things. The file is meant for Java code, and you'll have to tweak it a bit to work on any generic file.

---

### Post by laptoplinux on 2008-02-05
I appreciate the file, but is there any chance that someone knows about a more minimal approach.  I don't really understand all of the .emacs syntax at this point, and I don't have time to pick apart a highly specific file and mod it for a more general approach while trying to both get it working and not break my .emacs file.

---

