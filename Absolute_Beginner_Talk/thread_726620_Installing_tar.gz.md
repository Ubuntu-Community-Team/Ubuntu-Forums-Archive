---
title: "Installing tar.gz"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-16
How to install it?i use './configure" and then when i use "make" there is an error msg saying no targets found

---

### Post by bsharp on 2008-03-16
there should be a README file in the archive, take a look at that for more specific instructions.

---

### Post by steveneddy on 2008-03-16
> **adi_das said:**
> How to install it?i use './configure" and then when i use "make" there is an error msg saying no targets found

What does the "Read Me" file in the folder say to do?

---

### Post by Locutus_of_Borg on 2008-03-16
are you in the directory containing the makefile when you type make?

---

### Post by PeterJS on 2008-03-16
Also generally the configure script creates the Makefile, so if ./configure fails (which it is likely to do the first couple of times as you'll need to install various -dev packages) then there won't be a Makefile for make to run.

---

### Post by dynamethod on 2008-03-16
sorry delete this, my bad

---

### Post by aysiu on 2008-03-16
What are you trying to install?

---

