---
title: "Can't install Draftsight 12.04 32bit"
date: 2013-05-21
forum: Art &amp; Design
---

### Post by max230664 on 2013-05-21
Can you help me?
I have download draftsight.deb but when i installed it there are problem:

```
max@max:~$ sudo dpkg -i draftSight.deb(Lettura del database... 207333 file e directory attualmente installati.)
Preparativi per sostituire dassault-systemes-draftsight v.2013.1.56 (utilizzando draftSight.deb)...
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host
access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
Estrazione del sostituto di dassault-systemes-draftsight...
dpkg: problemi con le dipendenze impediscono la configurazione di dassault-systemes-draftsight:
 dassault-systemes-draftsight dipende da libgl1-mesa-glx (>= 7.6.0-1), ma:
  Il pacchetto libgl1-mesa-glx non è installato.
dpkg: errore nell'elaborare dassault-systemes-draftsight (--install):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 dassault-systemes-draftsight



```

---

### Post by gordintoronto on 2013-05-21
Run the Ubuntu Software Center, install libgl1-mesa-glx, then install Draftsight.

---

### Post by max230664 on 2013-05-22
> **gordintoronto said:**
> Run the Ubuntu Software Center, install libgl1-mesa-glx, then install Draftsight.

Thank you gordintoronto!
Ubuntu Software Center say me that libgl1-mesa-glx depend of libgl1-mesa-dri, i have install it, after i have reinstalled draftsight and now it's all ok!!!!

---

