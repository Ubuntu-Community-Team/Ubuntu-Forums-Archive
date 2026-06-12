---
title: "vi-fortran"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by NiTsi on 2005-12-01
when i write a program in fortran using vi it doesn't highlight with different colors as it should do.Any help?

---

### Post by ape on 2005-12-01
1. Ensure that you are using vim and not some other alternative to vi (nvi, etc). 

2. Does syntax highlighting work for any other source code (shell, perl, java...)?

3. What is the extension of the file you are attempting to edit?

---

### Post by NiTsi on 2005-12-02
[QUOTE=ape]1. Ensure that you are using vim and not some other alternative to vi (nvi, etc). 

2. Does syntax highlighting work for any other source code (shell, perl, java...)?

3. What is the extension of the file you are attempting to edit?[/QUOTE]



I don't any other languages so i can't tell about the second the first is ok .i'm using vim. the extension of the filename is .f

---

### Post by kont.raen on 2005-12-02
[QUOTE=NiTsi]I don't any other languages so i can't tell about the second the first is ok .i'm using vim. the extension of the filename is .f[/QUOTE]

Create / modify the file .vimrc in your home directory and add the line

syntax on

to the file - that should do the trick :)

---

### Post by NiTsi on 2005-12-03
[QUOTE=kont.raen]Create / modify the file .vimrc in your home directory and add the line

syntax on

to the file - that should do the trick :)[/QUOTE]


ok i did it and it works just fine (but i think that you knew it,didn't you? )
thanx

---

