---
title: "Where is the SQL data base stored?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by welshboy on 2006-10-04
Hi folks, your friendly welshman is back with YET another question!!

I'm using mySQL to write me data bases (of course), however I was wondering if there's a way to change where the data bases are stored, as I intend to use them in conjunction with some Java programs I'm writing.

Many thanks, and I hope everyone's doing ok tonight (or this morning, or this afternoon, wherever you are :) )

welshboy

---

### Post by welshboy on 2006-10-05
anybody?

---

### Post by sbergman27 on 2006-10-05
You can edit /etc/mysql/my.cnf.

---

### Post by Ueland on 2006-10-05
> **welshboy said:**
> Hi folks, your friendly welshman is back with YET another question!!

I'm using mySQL to write me data bases (of course), however I was wondering if there's a way to change where the data bases are stored, as I intend to use them in conjunction with some Java programs I'm writing.

Many thanks, and I hope everyone's doing ok tonight (or this morning, or this afternoon, wherever you are :) )

welshboy


They are as default stored at /var/mysql/data/"databasename"/"tables"" :)

---

### Post by welshboy on 2006-10-05
ok, I've found the file, but what do I edit?

---

### Post by sbergman27 on 2006-10-05
datadir         = /var/lib/mysql

BTW, do you have a link to a higher res version of your avatar? 
I'm a big NCC-1701 refit fan.

---

### Post by welshboy on 2006-10-05
Hey dude,

I edited it, and it still didn't put it in the right place sadly.  But there you go.

Still, nice to meet another Trek fan :)

I got the image from:

[http://www.30doradus.org/spaceships/images/1701e.jpg](http://www.30doradus.org/spaceships/images/1701e.jpg)

It's not that high res sadly, I'm in the hunt for a bigger one :)

welshboy

---

### Post by sbergman27 on 2006-10-05
Oh, it's the E.  I really liked the E. A lot better than the D.

But it's the 1701 refit from STTMP that is the love of my life... no bloody A, B, C, or D! [-(

---

### Post by welshboy on 2006-10-05
Try this one then ;) :P

[http://www.solace.mh.se/~el302/startrek/pics2/nc1701a.jpg](http://www.solace.mh.se/~el302/startrek/pics2/nc1701a.jpg)


welshboy

---

