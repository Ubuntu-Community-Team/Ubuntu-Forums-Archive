---
title: "How do I edit /etc/sane.d/dll.conf"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-05-11
I tried using sudo edit & I get a message about mime.

---

### Post by compmodder26 on 2007-05-11
you want "sudo gedit", note the "g".

edit: technically that should be "gksudo gedit".  If you really want to edit on the command line, use "sudo nano"

---

### Post by gh0st on 2007-05-11
> **captgadget said:**
> I tried using sudo edit & I get a message about mime.

Maybe try this

```

sudo nano /etc/sane.d/dll.conf 
```

or if you want a nice GUI and not a terminal based editor

```
sudo gedit /etc/sane.d/dll.conf

```
I assume it's a text file you are working on. Haven't looked at that file before myself. Dunno if that will help just thought I'd suggest it anyway. Good luck :)

---

### Post by heimo on 2007-05-11
This command should open it for editing:
```
gksudo gedit /etc/sane.d/dll.conf
```


EDIT: Doh. I'm terrible late. :) Time to get some sleep.

---

### Post by mazirian on 2007-05-11
I don't really understand the drive to open any X apps with superuser privileges.  A more traditional way of editing privileged text files is simply "sudo -e filename", which will evoke $EDITOR and be sure to open the file with write privileges.

---

### Post by heimo on 2007-05-11
> **mazirian said:**
> I don't really understand the drive to open any X apps with superuser privileges.  A more traditional way of editing privileged text files is simply "sudo -e filename", which will evoke $EDITOR and be sure to open the file with write privileges.

Which by default would be... vim? And we're now on Absolute Beginner Talk forum, where we try to make things as easy as possible. Graphical editors, like gedit make editing files a lot easier for beginners. Personally? I use vim.

---

### Post by Foxmike on 2007-05-11
> **mazirian said:**
> I don't really understand the drive to open any X apps with superuser privileges.  A more traditional way of editing privileged text files is simply "sudo -e filename", which will evoke $EDITOR and be sure to open the file with write privileges.

Just by curiosity, is there any security issue by opening X apps with superuser privileges?  Becuase if $EDITOR is vim, then a new user might be lost a bit...:)

Regards,

-FM

---

### Post by Foxmike on 2007-05-11
@heimo: you fast typer!:)

---

### Post by mazirian on 2007-05-11
What is the default $EDITOR for ubuntu anyway?  Probably nano, which isn't too bad.  But, yeah, you have a point.  To answer your question, however, I'm not really sure anymore.  It's just a so-called best practice I was always taught back in the days of xfree.

---

### Post by heimo on 2007-05-11
default $EDITOR is empty, which translates to vim, or more specifically "vim-tiny", emacs is not installed by default

---

### Post by captgadget on 2007-05-11
thanx - got 'er done

---

