---
title: "How to apply .patch"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by bobgreen5s on 2006-06-23
I have the need to apply/run a .patch file. How would I go about doing this?

---

### Post by Apple 101 on 2006-06-23
In a command prompt (terminal window):

patch -p0 < filename.patch

---

### Post by bobgreen5s on 2006-06-23
:)

---

### Post by bobgreen5s on 2006-06-23
thanks for the prompt reply :)

also: is it possible that different patches require different values for x if patch -px or does x always equal 0

---

### Post by Apple 101 on 2006-06-23
Usage: patch -px < filename.patch

The x value of -px can be any number.  It represents how many directories to take off from the patch.  Most of the time it will be x=0 though.  For more information and other patch commands, see *man patch*.

---

### Post by bobgreen5s on 2006-06-23
OK, thanks :mrgreen:

---

