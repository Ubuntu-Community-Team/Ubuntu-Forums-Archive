---
title: "[SOLVED] no file extensions?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by paranoid_humanoid on 2008-03-31
after being a devoted windows user for like 10 years, i started using ubuntu seriously a few days ago.
the first thing that came to my surprise was that most of the files have no file extension, and yet nautilus can recognize the format very easily..
how is that?

---

### Post by stchman on 2008-03-31
> **paranoid_humanoid said:**
> after being a devoted windows user for like 10 years, i started using ubuntu seriously a few days ago.
the first thing that came to my surprise was that most of the files have no file extension, and yet nautilus can recognize the format very easily..
how is that?

If you right click on the file and go to Properties then Open With you will see.

You can change that attribute easily.

---

### Post by Steveway on 2008-03-31
In Linux we don't need fileexensions to see what a file is.
We just let the system look at the file and check what it is according to it's content.
You can use the file-command in a terminal to test this.
> steveway@localhost:~$ file whooo.png
whooo.png: PNG image data, 600 x 214, 8-bit/color RGBA, non-interlaced

See? You get detailed information about the file.

---

### Post by original_jamingrit on 2008-03-31
You'll notice that in Linux, that three character extensions are more of a suggestion than a rule.    Nautilus is also able to detect when files might be misrepresenting themselves as well.  If you want to read more, check out their wiki at [http://live.gnome.org/Nautilus](http://live.gnome.org/Nautilus).

---

### Post by Daniel G. Taylor on 2008-03-31
Before DOS and Windows artificially imposed the whole 8.3 file naming conventions which where the result of some design decisions in the filesystems in use (FAT) on those systems, most everyone used the "magic bit" signature on files, which is still in use in some formats today. The way it works is the first few bytes of a file describe the format. A pretty common example used in Linux/Unix is for shell scripts, which almost always begin with '#!' and then a path to an interpreter, such as '#!/bin/bash' or '#!/usr/bin/env python' which tells your shell how to run the program below.

What happens with Nautilus these days is it will scan filenames for known extensions and scan files with no extensions. I believe it also scans files when you click on them, which can have the side effect of changing the icon as more information about the file is discovered. The approaches both have advantages and disadvantages, for instance the magic bit takes extra time to open and scan files, but definitively tells you what the file is (well, it can be faked, but I digress). This is why nautilus uses both methods and will try its best to open any file you throw at it.

If you are more interested try opening files in a hex editor some time. I think most image formats have the extension as capital letters for the magic bits, e.g. PNG for .png and such. I think Windows executables use PE, but I'm not sure. Fun stuff :)

---

### Post by Oldsoldier2003 on 2008-03-31
although file extensions are not required in most cases in Linux, we do commonly use them in order to keep things straight.

.o is a compiled executable program
.sh is a shell script
.conf is a configuration

etc...

 another thing to remember is Linux is case sensitive so "Document.txt" is a different than "document.txt"

Also we have hidden files and directories. These are files or directories that start with a  "." such as ".profile" . You can see these files by toggling view hidden files in nautilus (ctrl +H) or using the -a flag with the ls command "ls -a".

---

### Post by Ardrias on 2008-03-31
This is a good place to read up a bit: [http://en.wikipedia.org/wiki/MIME](http://en.wikipedia.org/wiki/MIME)

---

### Post by rolnics on 2008-03-31
Wow this is a great read guys! You learn something new everyday = ls -a!!

---

