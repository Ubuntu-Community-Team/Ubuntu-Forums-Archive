---
title: "Where Is My wine Directory?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-06-29
I've installed wine and want to use Nautilus to view the directory and copy some files into it. I can see the directory in terminal: 

[email]sleestack@laptop:/.wine[/email]$

I can even do a listing: 

[email]sleestack@laptop:/.wine[/email]$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg

But when I go to my home directory in Nautilus I don't see it. Any suggestions?

---

### Post by cwood06 on 2007-06-29
its in ~/.wine/drive_c/Program\ Files/

you can copy your files into there

if its your first run do a winecfg in a terminal first to create the directorys

---

### Post by Sleestack on 2007-06-29
Thanks for your quick reply.  I ran wincfg, it created the directories. I can list some files, but it still doesn't show up in Nautilus. 

sleestack@laptop:~$ cd .wine
[email]sleestack@laptop:~/.wine[/email]$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
[email]sleestack@laptop:~/.wine[/email]$ 

Shouldn't I be seeing the wine directory in Nautilus from within my home folder?

---

### Post by Mr Greencastle on 2007-06-29
You can, its just marked as a hidden folder in your home directory.

Hit CTRL+H to see them, it should be under '.wine'

Regards,
Mr Green

---

### Post by vexorian on 2007-06-29
all folders and files that begin with . are not listed by nautilus unless you check show hidden files

---

### Post by Sleestack on 2007-06-29
That's it! Much appreciated.

---

