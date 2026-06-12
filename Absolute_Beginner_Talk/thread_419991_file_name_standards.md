---
title: "file name standards"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by actioncomics on 2007-04-23
I was wondering if someone could tell me or point me in the right direction for filename standards for linux.  I will have be to working in Linux(home) and Windows(work) so i don't want naming conflicts.  specifically i need to know are parentheses ok in linux and are spaces ok.  I will be working in a terminal window also, so as little typing as possible, i think i read somewhere that you have to put quotes around a filename if there are spaces in the name.  thank for any help/clarification.

ac

---

### Post by jasonlfunk on 2007-04-23
[http://www.tuxfiles.org/linuxhelp/weirdchars.html](http://www.tuxfiles.org/linuxhelp/weirdchars.html)

This looks like it answers most of your questions.

---

### Post by Snowcat on 2007-04-23
Parentheses and spaces are both fine.

To access something with spaces through a terminal screen:

cd 'folder with spaces'/

or:

cd folder\ with\ spaces/

etc.

---

### Post by silverglade00 on 2007-04-23
```
gedit "Unsaved (Document) 1"
```

This works fine on my system. You are correct that you need the quotes. I remember it being the same in Windows.

---

### Post by actioncomics on 2007-04-23
perfect thanks for the info.

---

### Post by huggy77 on 2007-08-24
on this subject

i have noticed that i have problems with samba sometimes - folder names get concatenated...

is that a result of the length of the filename or the spaces in the filename...  I am not sure...

EITHER WAY - IF YOU ARE USING SAMBA, i think you have to avoid large filenames...

i actually set up appletalk on my network - and i have no more problems...

---

