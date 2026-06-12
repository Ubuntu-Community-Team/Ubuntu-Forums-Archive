---
title: "install from tar.gz on Xubuntu"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-05-10
Hi,
I'm trying out Xubuntu for fun!  But I can't figure out how to install a downloaded package (osb browser) which comes as a tar.gz  Do I need to install an archive manager first, or can I do it from the command line, if so what do I type?

Thanks

---

### Post by mostwanted on 2006-05-10
Here ya go:

[http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)

---

### Post by damianubuntu on 2006-05-10
sorry if I'm being thick here, but don't I have to unpack the archive first, before cofigure, make whatever....  In Xubuntu I don't have the right-click extract here option.

---

### Post by mostwanted on 2006-05-10
[QUOTE=damianubuntu]sorry if I'm being thick here, but don't I have to unpack the archive first, before cofigure, make whatever....  In Xubuntu I don't have the right-click extract here option.[/QUOTE]

Either open it in some archiver manager and unextract it, or do this in the terminal

```

tar -xzfv /path/to/package
```

---

### Post by aysiu on 2006-05-10
[QUOTE=damianubuntu]sorry if I'm being thick here, but don't I have to unpack the archive first, before cofigure, make whatever....  In Xubuntu I don't have the right-click extract here option.[/QUOTE] That's precisely why graphical tutorials stink--they may be "easy," but they don't apply to all situations.

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

No offense to MonkeyBlog--I link to that all the time, and I'm grateful it exists, but it is very limited in application.

---

### Post by Kimm on 2006-05-10
You can extract in your terminal:

tar xvzf <archive>.tar.gz

if its a .tar.bz2 its:

tar xvjf <archive>.tar.bz2

---

### Post by damianubuntu on 2006-05-10
thanks everyone.  BTW I also wanted to upgrade my Xubuntu to Dapper, I guess its better to do this before installing the new browser?  And can I get Xubuntu Dapper with 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

or am I all confused, what with a little knowledge being a dangerous thing?!!

---

### Post by aysiu on 2006-05-10
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by damianubuntu on 2006-05-10
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)[/QUOTE]

Thanks, now that's what I call complete instructions!:-D

---

