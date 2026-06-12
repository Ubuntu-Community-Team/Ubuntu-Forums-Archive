---
title: "Problems updating firefox"
date: 2005-05-17
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-05-17
Hi guys.

Am I the only one who is experiencing problems trying to update firefox to 1.0.4 through ubuntu's software upgrade tool?

The server from which Im trying to download is really slow and cant finish the downloading...

Help guys!

Thanks!

---

### Post by zaxer on 2005-05-17
I got this message

> 
W: Falló al obtener [http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/mozilla-firefox_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb](http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/mozilla-firefox_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb)
  503 Service Unavailable


---

### Post by jodef on 2005-05-17
Have a look here : [Backport Mirrors](http://www.ubuntuforums.org/showthread.php?p=174918#post174918) and here : [Why backports slow](http://www.ubuntuforums.org/showthread.php?t=33307)

---

### Post by zaxer on 2005-05-17
[QUOTE=jodef]Have a look here : [Backport Mirrors](http://www.ubuntuforums.org/showthread.php?p=174918#post174918) and here : [Why backports slow](http://www.ubuntuforums.org/showthread.php?t=33307)[/QUOTE]
 Ok.

I see wheres the problem.

Thanks for the info Jodef

---

### Post by zaxer on 2005-05-17
How can I add this line to my sources.list?

[ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/)

---

### Post by jodef on 2005-05-17
From the terminal type : 
**sudo cp /etc/sources.list /etc/sources.list.original** this is just to create a backup copy incase you need to restore later, next type **sudo gedit /etc/sources.list**  copy and paste the line at the bottom of the opened file and save. Now go to synaptic and reload.

---

### Post by zaxer on 2005-05-18
[QUOTE=jodef]From the terminal type : 
**sudo cp /etc/sources.list /etc/sources.list.original** this is just to create a backup copy incase you need to restore later, next type **sudo gedit /etc/sources.list**  copy and paste the line at the bottom of the opened file and save. Now go to synaptic and reload.[/QUOTE]

I think its /etc/apt/sources.list

by the way, do I have to write deb or something before [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) ¿?

Thanks

---

### Post by jodef on 2005-05-18
Yeah sorry about that. I'll check that later late for work if someone else doesn't answer first.

---

### Post by zenlord on 2005-05-18
[QUOTE=zaxer]Am I the only one who is experiencing problems trying to update firefox to 1.0.4 through ubuntu's software upgrade tool?[/QUOTE]
My Ubuntu install didn't find any updates for firefox (probably because I hadn't expanded my sources.list-file), so I went ahead and:
1. removed firefox with Synaptic;
2. downloaded and installed the official tarball from mozilla.org.

Is this 'not done' in debian-based distro's? Is this really ugly, or is it just a cosmetic difference?

Zl. (yaLn - yet another Linux-n00b)

---

### Post by jdong on 2005-05-18
to switch mirrors, replace all instances of [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) with [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) in your /etc/apt/sources.list.


As far as downloading a tarball from Mozilla.org, that is really **NOT** a smart way to upgrade. Ubuntu makes many customizations on top of Firefox, especially to blend into Ubuntu/Debian. Other packages, like Epiphany/Galeon/Mono, depend on these customizations.


Bypassing the package manager won't get you all the features you'd want.

---

### Post by zaxer on 2005-05-18
[QUOTE=jdong]to switch mirrors, replace all instances of [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) with [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) in your /etc/apt/sources.list.
[/QUOTE]

Can you show  me how it finally looks in the sources.list?

Thanks.

---

### Post by LongTooth on 2005-05-18
I've had no problems with Ubuntu's Update Manager. It upgrade Firefox to the latest 1.0.4. But I do see a slow down in speed. Done anyone else notice this? Is there a way to speed it it up? If you've got any tips that might help, let us know. Thanks.

---

### Post by jdong on 2005-05-18
The slowdown is due to a bandwidth cap we placed to avoid overtime charges for our server. Try mirrors.

---

### Post by zaxer on 2005-05-18
[QUOTE=LongTooth]I've had no problems with Ubuntu's Update Manager. It upgrade Firefox to the latest 1.0.4. But I do see a slow down in speed. Done anyone else notice this? Is there a way to speed it it up? If you've got any tips that might help, let us know. Thanks.[/QUOTE]
 I downloaded it today at 10.00 am GMT+1 at 10kbps speeds...

---

