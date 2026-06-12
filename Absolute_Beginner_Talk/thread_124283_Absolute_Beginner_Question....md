---
title: "Absolute Beginner Question..."
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2006-02-01
Hello People,
.tar.gz is which format? Can any file with that format be directly installed in Ubuntu without using alien?
Thanks,
Linuxnovice.

---

### Post by Perfect Storm on 2006-02-01
.tar.gz is like a .zip files you have in windows. Usually when you find a application in that format it contains the source so you can compile it.

---

### Post by geekphreak on 2006-02-01
The tar part of it comes from the fact that a file is tape-archived, and the gz part means that it was zipped using GNU zip utility.

---

### Post by cotcot on 2006-02-01
tar.gz must be extracted by using tar xvf filename.
Then you must change to the extracted files. In this directory you can find a file containing instruction to install (compile) generally in INSTALL, read also README.   Most of the time you have top use
                        ./configure
                        make
                        sudo make install
Easier is the package install program SYNAPTIC. Please read about it the documentation.

---

### Post by steve.horsley on 2006-02-01
[QUOTE=cotcot]tar.gz must be extracted by using tar xvf filename.[/QUOTE]

Minor correction: a file called for instance my-pr0n.tar.gz would be un-zipped with the command **tar xvfz my-pr0n.tar.gz**.  The extension is sometimes shortened to **.tgz** - it's the same thing. 

You can also extract with nautilus by right-clicking the file and choosig Extract Here.

Beware, these files will usually unzip to produce a folder full of stuff, but only if the maker zipped that folder up in the first place. It may contain just a collection of files that are not tucked into their own folder, in which case your current directory will get all thos files dumped into it. This can take quite a lot of cleanup, so its always worth looking inside first. From the command line you can list the contents with **tar tvfz my-pr0n.tar.gz**, or in Nautilus, right-click and select to open with Archive Manager.

---

### Post by linuxnovice on 2006-02-03
Thankyou people.
Linuxnovice.

---

