---
title: "Opera won't start"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Rafinator on 2006-09-26
After installing armagetron, I cannot open up opera web browser.  I tried un-installing, but that didn't do anything.  Then I tried going into the terminal and just typing 'opera' I got this error.

```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.02-20060919.6/opera: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: 

```
any idea's how do fix this?

---

### Post by whizbaby on 2006-09-26
Backup your opera config directory
cp -r .opera .opera.old
and remove opera. Reinstall it and
cp -r .opera.old .opera

---

### Post by Rafinator on 2006-09-26
```
rafinator@ubuntu:~$ cp -r .opera.old
cp: missing destination file operand after `.opera.old'
Try `cp --help' for more information.

```

that happens when I try the first command.

---

### Post by whizbaby on 2006-09-26
Try copy-pasting with more accuracy (you left out .opera).

---

### Post by Rafinator on 2006-09-26
Did that, still have the same errors.

I found some stuff 
here: [http://my.opera.com/community/forums/topic.dml?id=159159](http://my.opera.com/community/forums/topic.dml?id=159159)
on the whole thing, but I can't understand it.  Also a google search of the problem takes you to the same problem on a gentoo forum.  I have no idea what to do.

I also did a complete un-install.  now there is no .opera folder, and I still get the same error.

---

### Post by whizbaby on 2006-09-26
Sorry I left out a **/**
cp -r .opera/ .opera.old
and remove opera. Reinstall it and
cp -r .opera.old/ .opera
(just typed in my own terminal so this is guaranteed to work)

---

### Post by Rafinator on 2006-09-26
> **whizbaby said:**
> Sorry I left out a **/**
cp -r .opera/ .opera.old
and remove opera. Reinstall it and
cp -r .opera.old/ .opera
(just typed in my own terminal so this is guaranteed to work)

no such folder as .opera, it's not there anymore.

---

### Post by whizbaby on 2006-09-26
O.k., so you got no personal config of opera? Doesn't matter, reinstalling won't solve it. I was wondering why my opera is running well and discovered the libawt.so and libjvm.so on my computer, they belong to the sun-java environment, so installing this perhaps helps opera finding them. The package name is 
*sun-java5-jre*
and you need universe/multiverse enabled.

---

