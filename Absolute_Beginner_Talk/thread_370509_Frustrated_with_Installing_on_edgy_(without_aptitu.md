---
title: "Frustrated with Installing on edgy (without aptitude)"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-02-25
I am trying to install a program called juploadr (its used with Flickr) and I cannot find it in Aptitude, and I have all reciprocities enabled. I have downloaded the tar.gz, and I am trying to follow the directions on [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) AND [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) and once i get to the "make" command I get this result

make: *** No targets specified and no makefile found.  Stop.

Could someone please try to explain to me how to install something manually.

Thanks

Monica:confused:

---

### Post by nyinge on 2007-02-25
What errors do you get after ./configure?  Have you got Sun's java installed yet?  juploadr requires java from Sun.

---

### Post by picpak on 2007-02-25
[juploadr_1.0-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/juploadr_1.0-3v1ubuntu0_i386.deb)

Is this what you're looking for?

---

### Post by nyinge on 2007-02-25
Awesome :)  That package should do the trick.

---

### Post by mkjarema on 2007-02-26
thank you so much!
the .deb worked perfectly.  I am going to put Sun's Java in also.

Thanks so much, I am trying so hard to make Ubuntu work for me. I am not giving up, thanks again for your help

---

### Post by mkjarema on 2007-02-26
is it javacc in the package manager that i need?

thx

---

### Post by nyinge on 2007-02-26
When you install the jUploadr deb package, does it complain anything?

---

### Post by mkjarema on 2007-02-27
nope, it went right in.  I also already have Java Sun installed 5.0

thx

---

