---
title: "[SOLVED] unlink linked files"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-15
While in my home directory I accidentally marked the link choice in the right click menu. I noticed that this "linked the files to programs. Still thinking M$ (i've had it since dos days) I marked it again thinking it was a toggle. Now I have "link to link to" on the files. How can I get rid of this and restore to original condition??:confused:

---

### Post by SpiritIsReality on 2007-09-15
howdy
I haven't done much with links yet, but if you open up a terminal,
applications>accessories>terminal and then type in
```
ls -la
```and press enter. it should list all the files in your home directory.
the ones starting with an "L" are links. you could delete them. so it says
here
[https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html#nautilus-symlink](https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html#nautilus-symlink)
welcome back to the good old days of the command line.

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html#nautilus-symlink](https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html#nautilus-symlink)
[http://linuxcommand.org/](http://linuxcommand.org/)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=command&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=command&titlesearch=Titles)

and in the ubuntuforums.org advanced search, you can search the tips and tutorials
forum for commandline or ?

you don't have to use the terminal, but it helps.

trails

---

### Post by nick_h on 2007-09-15
If you highlight some files and then right click and select "Make Links" links will be created with "Link to " added to the begining of the file names.  These links are just pointers to the original files and if you delete them the original files will remain.  Just highlight them and press the delete key.

---

### Post by skyjacker on 2007-09-15
> **nick_h said:**
> If you highlight some files and then right click and select "Make Links" links will be created with "Link to " added to the begining of the file names.  These links are just pointers to the original files and if you delete them the original files will remain.  Just highlight them and press the delete key.
Thanks - Just what I needed to do.   Ubuntu rocks:guitar:

---

