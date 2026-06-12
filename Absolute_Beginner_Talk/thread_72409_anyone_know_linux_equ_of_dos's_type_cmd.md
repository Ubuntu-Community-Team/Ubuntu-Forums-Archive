---
title: "anyone know linux equ of dos's type cmd?"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-06
Just what the title says :)

or better yet is it possible to list the contents of a text file online and dimp it to terminal?

---

### Post by mpat on 2005-10-06
dos' type is linux' "cat": **cat <filename>**. But maybe you will prefer **less**, where you can scroll thru the file's content using pgup and pgdown.
If you want to view the content of an online file you might use wget:

**wget -qO - [http://www.whatever.com/](http://www.whatever.com/)**

If you want the output to be scrollable use a pipe thru less:

**wget -qO - [http://www.whatever.com/](http://www.whatever.com/) | less**

Hope that helps you!

---

### Post by nitricacid on 2005-10-06
try this site [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

