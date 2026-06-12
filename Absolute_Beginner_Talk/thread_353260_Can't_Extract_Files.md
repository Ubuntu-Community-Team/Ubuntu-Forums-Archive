---
title: "Can't Extract Files"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Kerry Lange on 2007-02-04
I'm trying to install a printer and some of the files come in a "*.tar.Z" package.  The file archiver doesn't know what to do with the file.  I get the following error message:

Could not open "*.tar.Z" Archive type not supported.

When I remove the ".Z" from the end of the file name, a folder gets created but there's an error message and nothing gets put in the folder (i.e. no files are extracted).

The file contains PPDs for a Lexmark printer.

Suggestions?

---

### Post by Paerez on 2007-02-04
open a terminal and type:
"file whateveritscalled.tar.Z"
that should tell you what kind of zip it is. Then post that here.

---

### Post by annda on 2007-02-04
on the lexmark site it says you need to uncompress the archive by typing

uncompress your_ppd_filename

this command should produce an archive which you can open by double click

---

### Post by ComplexNumber on 2007-02-04
get the original file(with the Z part left on). then go to the command line and cd to where the file is. then type in 'uncompress <filename>'(the filename ending in whatever.tar.Z). then tar -xvf <filename>'(the filename ending in whatever.tar)

EDIT: seems like a few have got there before me. d'oh!

---

### Post by Kerry Lange on 2007-02-04
> **Paerez said:**
> open a terminal and type:
"file whateveritscalled.tar.Z"
that should tell you what kind of zip it is. Then post that here.

Here's what I get:

PPD-Files-LMABO.tar.Z: compress'd data 16 bits

---

### Post by Kerry Lange on 2007-02-04
> **ComplexNumber said:**
> get the original file(with the Z part left on). then go to the command line and cd to where the file is. then type in 'uncompress <filename>'(the filename ending in whatever.tar.Z). then tar -xvf <filename>'(the filename ending in whatever.tar)

EDIT: seems like a few have got there before me. d'oh!

Your suggestion worked!  The files extracted as needed.  Thanks to both of you!

Why would the file be structured that way?  Why compress the file so that there are two steps like that?

---

### Post by Kerry Lange on 2007-02-04
> **annda said:**
> on the lexmark site it says you need to uncompress the archive by typing

uncompress your_ppd_filename

this command should produce an archive which you can open by double click

Crap.  I missed that.  Thanks for pointing it out.

---

