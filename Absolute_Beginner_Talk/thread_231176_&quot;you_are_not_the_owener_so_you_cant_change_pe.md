---
title: "&quot;you are not the owener so you cant change permissions&quot;"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by DesertFox on 2006-08-07
i need to edit a system file but i cant save it cause it set as read only and it tells me that i am not the owner so i cant change the file permissions

---

### Post by graysnake on 2006-08-07
open a terminal
sudo chmod 777 (or another combination)
now you can edit the file

---

### Post by moma on 2006-08-07
$ sudo gedit afilename
$ gksudo gedit afilename

Use kate or kwrite if you run KDE.

---

### Post by mcduck on 2006-08-07
> **graysnake said:**
> open a terminal
sudo chmod 777 (or another combination)
now you can edit the file

It's not very wise to change permissions of system files. Most likely it would break your system..

---

### Post by Skia_42 on 2006-08-07
Just use> sudo gedit <file>

---

### Post by Christmas on 2006-08-07
Better yet "gksudo gedit filename".

---

### Post by asfx on 2006-08-07
> **Skia_42 said:**
> 
Just use
  Quote: sudo gedit <file>


Just a little extra info. This helped me.
The "sudo" command gives root(I think) permission
to whatever you type after it, be it a program like 
gedit or a a system command. 

This is quite basic for most users but not so clear to noobs
like me, and having it explained helped. :)

---

