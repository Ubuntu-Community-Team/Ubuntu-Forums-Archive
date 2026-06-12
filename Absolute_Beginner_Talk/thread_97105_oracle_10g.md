---
title: "oracle 10g"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by ziociccio on 2005-11-30
Hi, 

many problems with oracle.

I tried installation with [http://www.csee.wvu.edu/~ccole/oracle10g-ubuntu](http://www.csee.wvu.edu/~ccole/oracle10g-ubuntu) but it doesn't work.

I downloaded other package from debian site but gcc3.3 requires libstdc++5-3.3-dev... and libstdc++5-3.3-dev needs gcc3.3!!!!

is it possibile???
Look:
francesco@acerubuntu:~/Desktop$ sudo dpkg -i libstdc++5-3.3-dev_3.3.6-7_i386.deb
(Lettura del database ... 78127 file e directory attualmente installati.)
Mi preparo a sostituire libstdc++5-3.3-dev 1:3.3.6-7 (con libstdc++5-3.3-dev_3.3.6-7_i386.deb) ...
Spacchetto il rimpiazzo di libstdc++5-3.3-dev ...
dpkg: problemi con le dipendenze impediscono la configurazione di libstdc++5-3.3-dev:
 libstdc++5-3.3-dev dipende da g++-3.3 (>= 1:3.3.6-7); comunque:
  Il pacchetto g++-3.3 non è ancora configurato.
dpkg: errore processando libstdc++5-3.3-dev (--install):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 libstdc++5-3.3-dev
francesco@acerubuntu:~/Desktop$ sudo dpkg -i g++-3.3_3.3.6-10_i386.deb
(Lettura del database ... 78127 file e directory attualmente installati.)
Mi preparo a sostituire g++-3.3 1:3.3.6-10 (con g++-3.3_3.3.6-10_i386.deb) ...
Spacchetto il rimpiazzo di g++-3.3 ...
dpkg: problemi con le dipendenze impediscono la configurazione di g++-3.3:
 g++-3.3 dipende da libstdc++5-3.3-dev (= 1:3.3.6-10); comunque:
  La versione di libstdc++5-3.3-dev nel sistema è 1:3.3.6-7.
dpkg: errore processando g++-3.3 (--install):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 g++-3.3


any suggestions??

I don't have internet access.

---

