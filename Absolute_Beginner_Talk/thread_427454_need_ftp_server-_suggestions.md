---
title: "need ftp server- suggestions?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by ben0r on 2007-04-29
So far, this linux stuff has been very complicated.  Why can't everything have a GUI? 

is there any ftpserver program I can use thats easy to setup?  I installed pure ftp but I cant find any clear documentation of how to get it setup right.  Any good how to guides out there?  I spent awhile googling and can't find anything I understand

suggestions?

---

### Post by taurus on 2007-04-29
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install proftpd gproftd
gksudo gproftpd
```

---

### Post by Bachstelze on 2007-04-29
> **ben0r said:**
> So far, this linux stuff has been very complicated.  Why can't everything have a GUI? 

Because no one has written one yet.

---

### Post by ben0r on 2007-04-29
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install proftpd gproftd
gksudo gproftpd
```

I also installed that via synaptic, but how do I configure the server?  I tried finding the .conf file, but never did. know of any good guides?

---

### Post by taurus on 2007-04-29
The last command from my previous post will fire up GUI configure tool for proftpd.  Here's the doc for it if you want to read through it.

[http://archiv.debianhowto.de/en/proftpd/c_proftpd.html](http://archiv.debianhowto.de/en/proftpd/c_proftpd.html)
or
[http://www.proftpd.org/](http://www.proftpd.org/)

---

### Post by ben0r on 2007-04-29
nice, did that via terminal, and i have a gui, yay!  let me play with this now :)

---

### Post by ben0r on 2007-04-29
got it up and running...and it works!

thanks.

---

### Post by giranmoo2 on 2007-04-29
Hmm, how do I configure this server with the cli interface? I thought I should give proftpd a go seeing as I'm using a much better linux distro.

---

