---
title: "What am I doing wrong..?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-10-18
tarchy@tarchy:~/Downloads/tovid-0.31$ sudo su -c "make install"
make: *** No rule to make target `install'.  Stop.
tarchy@tarchy:~/Downloads/tovid-0.31$ 


No rule to make target install? Grr what the heck

---

### Post by tarchy on 2007-10-18
Tut I'm using:

[http://tovid.wikia.com/wiki/Installing_tovid](http://tovid.wikia.com/wiki/Installing_tovid)

at .configure, it says this:

```
configure: error:

 ERROR:

 txt2tags cannot be found on your system, but tovid needs it to build
 the man pages. Please install txt2tags (http://txt2tags.sf.net) and
 run ./configure again. Thanks!

     -- http://tovid.org
```

And then I try install, and the error on my above post.

---

### Post by Soarer on 2007-10-18
Have you seen the install instructions for Ubuntu in this page...

[http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu](http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu)

It seems the debs are broken, but you could try using alien to get them from the rpm. Easier than compiling yourself.

BTW, txt2tags is in the Universe repository (at least on Gutsy) so you can install that first.

---

