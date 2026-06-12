---
title: "website archive program?"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by ephman on 2006-03-02
hi,

does anybody know of an application where i can insert an url, and it'll download the complete website in the directory hierarchy?  almost like a caching program?

thanks,
ephman

---

### Post by stalefries on 2006-03-02
Check out httrack. Or something like that.

---

### Post by az on 2006-03-02
[QUOTE=stalefries]Check out httrack. Or something like that.[/QUOTE]
emma@ubuntu:~$ apt-cache search httrack
httrack - Copy websites to your computer (Offline browser)
httrack-doc - Httrack website copier additional documentation
libhttrack-dev - Httrack website copier includes and development files
libhttrack1 - Httrack website copier library
webhttrack - Copy websites to your computer, httrack with a Web interface
emma@ubuntu:~$

Yep.  It works great.  If I remember, you need the webhttrack package, too

---

### Post by BoyOfDestiny on 2006-03-03
Don't forget wget! It comes with ubuntu...

type 
man wget

It has plenty of options, i.e. don't visit offsite links (so you don't suck up the whole web ;) ), make all links relative, ignore/retreive certain files, etc...

---

### Post by Jucato on 2006-03-03
I think those kinds of programs are called spiders?But please be considerate in using them, especially in downloading huge sites like forums. One of the forums that I go to has specifically requested not to do this since it has considerable effects on their servers.

---

