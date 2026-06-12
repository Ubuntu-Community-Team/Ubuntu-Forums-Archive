---
title: "amsn 0.98"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by rugby82 on 2007-12-31
hallo boy.....
i have try to download a new version of amsn svn 0.98........i have installed it whit:

./configure
make 
make install

and this is all true but when i try to use this command: make deb it show me this message:
```
dh_builddeb --destdir="./distrib/DEB" --filename="amsn_0.98b-svnesportato.deb"
dpkg-deb - errore: Debian revision (`svnesportato') non contiene cifre
dpkg-deb: 1 errori nel file di controllo
dh_builddeb: command returned error code 512
make[1]: *** [binary-arch] Error 1
make[1]: Leaving directory `/home/socket/Scrivania/amsn-0.97'
make: *** [deb] Error 2
```
what mean?

ps "non contiene cifre" mean that have not digit into file svnesportato!

---

### Post by stijngysemans on 2007-12-31
You do not have to build the deb file. After you've succesfully compiled and installed (make install) the program. You can just execute it via the terminal.

---

### Post by rugby82 on 2007-12-31
yes i know this, but.....i want to try to create a deb package

---

### Post by stijngysemans on 2007-12-31
I remember this error. you have to configure (somehow) a version of the deb. Each deb must have a version associated with it, otherwise it can't be generated.

---

### Post by rugby82 on 2007-12-31
mmhh....ok thank you!

---

### Post by rbernardes on 2008-02-20
I make a little tutorial how installaing amsn 0.98b (svn)
I hope this help!
[http://rmbernardes.wordpress.com/2008/02/20/amsn-098svn-com-antialising-no-ubuntu-710/](http://rmbernardes.wordpress.com/2008/02/20/amsn-098svn-com-antialising-no-ubuntu-710/)

---

