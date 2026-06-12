---
title: "Backup repositori &amp;&amp; programes instalats"
date: 2010-09-01
forum: Catalan Team
---

### Post by tanreb20 on 2010-09-01
Hola! COm que tinc pensat reinstalar el sistema d'aqui pocs dies m'agradaria saber com puc fer una copia de TOTS els repositoris que tinc instalats, i les seves respectives Claus RSA, i fer un llistat de tots els programes instalats per tal de poder recuperar-ho facilemnt desmpres.

ALguna idea?

---

### Post by wgarcia on 2010-09-02
Per obtenir un llistat de tot el que tens instal·lat i desar-lo en un fitxer:

dpkg --get-selections > software.instal·lat.log

Després si ho vols reinstal·lar un cop hagis reestablert el sistema i tinguis instal·lat el sistema base:

dpkg --set-selections < software.instal·lat.log
dselect 


"dselect" possiblement l'hagis d'instal·lar abans (sudo apt-get install dselect). S'ha de fer servir "i" per instal·lar el software.

---

### Post by tanreb20 on 2010-09-02
I alguna opció per tenir tots els repositoris?

---

### Post by wgarcia on 2010-09-02
Els repositoris els tens al fitxer:

/etc/apt.d/sources.list

Pots fer una còpia d'aquest fitxer i engantxar-lo a la nova instal·lació (sempre que no canviïs de versió d'Ubuntu, és clar).

---

### Post by tanreb20 on 2010-09-02
Pero i les claus RSA?

---

### Post by wgarcia on 2010-09-02
Són a Sistema -> Fonts de programari - Autentificació

---

