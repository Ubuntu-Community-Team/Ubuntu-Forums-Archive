---
title: "Printer Installation Question"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by brn on 2006-03-01
I just installed an Epson "Stylus C88" printer.  While this model was not specifically listed in the printer setup routine, I found the same behavior from others like C82, C83, C84, etc.  Printing from *gedit* or *Acrobat Reader *works fine.  But when I try "cat {filename} > lpr" iit fails, sending many page-ejects and occasional one-line   gibberish.  What am I doing wrong?

---

### Post by hoodwink on 2006-03-01
[QUOTE=brn]I just installed an Epson "Stylus C88" printer.  While this model was not specifically listed in the printer setup routine, I found the same behavior from others like C82, C83, C84, etc.  Printing from *gedit* or *Acrobat Reader *works fine.  But when I try "cat {filename} > lpr" iit fails, sending many page-ejects and occasional one-line   gibberish.  What am I doing wrong?[/QUOTE]
The behavior you want is

cat {filename} | lpr  (ie pipe the output to lpr)

---

