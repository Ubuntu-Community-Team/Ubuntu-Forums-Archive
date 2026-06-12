---
title: "Correzione dipendenze"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by remakeit on 2007-02-18
I have this error upgrading Avidemux from ubuntu version (2.1.x) to 2.3.
I can't recover the installation and i don't know how to resolve this problem.....
I had tried with apt-get -f install......this is the response....
If i try to remove Avidemux or some lib of dependencies all the packages are to removed....

 sudo apt-get -f install
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso
Reading state information... Fatto
Correzione delle dipendenze in corso... fallita.
I seguenti pacchetti hanno dipendenze non soddisfatte:
  avidemux: Dipende: libasound2 (> 1.0.12) ma 1.0.11-7ubuntu3 è installato
            Dipende: libc6 (>= 2.5-0ubuntu1) ma 2.4-1ubuntu12.3 è installato
            Dipende: libfontconfig1 (>= 2.4.0) ma 2.3.2-7ubuntu2 è installato
            Dipende: libgcc1 (>= 1:4.1.1-21ubuntu1) ma 1:4.1.1-13ubuntu5 è installato
            Dipende: libpango1.0-0 (>= 1.15.1) ma 1.14.5-0ubuntu1 è installato
            Dipende: libpng12-0 (>= 1.2.15~beta5) ma 1.2.8rel-5.1ubuntu0.1 è installato
            Dipende: libslang2 (>= 2.0.6-3) ma 2.0.6-2 è installato
            Dipende: libstdc++6 (>= 4.1.1-21ubuntu1) ma 4.1.1-13ubuntu5 è installato
  libxml2: Dipende: libc6 (>= 2.5-0ubuntu1) ma 2.4-1ubuntu12.3 è installato
  libxml2-dev: Dipende: libxml2 (= 2.6.26.dfsg-2ubuntu4) ma 2.6.27.dfsg-1ubuntu1 è installato
E: Errore, pkgProblemResolver::Resolve ha generato uno stop, questo può essere causato da pacchetti bloccati
E: Impossibile correggere le dipendenze

Impossible to correct the dipendecies......

Please.....someone to help me.....thank you in advance!

---

### Post by SadaraX on 2007-02-19
You can download it from [www.getdeb.net](www.getdeb.net) or you can try my custom Edgy version:
[http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb)

If you feel really daring you can try the latest development unstable version. The official statement by the developers concerning non-stable versions is "Do not use if you want to save what you make" basically meaning no there is no guarantee. If you can, I would say use version 2.3, but 2.4 will probably not hurt you (I use it all the time and it is pretty stable).
[http://students.washington.edu/cdobrich/avidemux_2.4.0_unstable_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.4.0_unstable_i386.deb)

---

