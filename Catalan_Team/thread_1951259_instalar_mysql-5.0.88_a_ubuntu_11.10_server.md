---
title: "instalar mysql-5.0.88 a ubuntu 11.10 server"
date: 2012-04-02
forum: Catalan Team
---

### Post by jaumety on 2012-04-02
Hola bon dia, tinc instalat ubuntu 11.10 server i m'agradaria saber com es fa per a instal·lar mysql-5.0.88 en lloc del mysql-5.1.41 que instal·la l'apt-get per defecte.

Gràcies.

---

### Post by wgarcia on 2012-04-02
Hauries de desintal·lar el mysql 

```
sudo apt-get remove mysql
```

anar al lloc on es pugui baixar el mysql, i mirar si tenen un arxiu "deb" per instal·lar. 

Si no hi hagués encara podries compilar i instal·lar tu mateix la versió que busques (funcionarà sempre i quan no entri en conflicte amb altres paquets actualitzats). 

Per últim si hi ha un fitxer "rpm" (un altre sistema de empaquetar aplicacions) podries utilitzar el programa "alien" a veure si l'aconsegueix instal·lar.

---

### Post by jaumety on 2012-04-03
He baixat els dos paquets MySQL-client-5.0.96-1.glibc23.x86_64.rpm i MySQL-server-5.0.96-1.glibc23.x86_64.rpm.
Ho he intentat instal·lar amb: 

sudo alien -iv MySQL-server-5.0.96-1.glibc23.x86_64.rpm
sudo alien -iv MySQL-client-5.0.96-1.glibc23.x86_64.rpm

... fa el procés d'instal·lació, però crec que no instal·la.
- Que podria provar?

---

### Post by wgarcia on 2012-04-03
Et dóna alguna error?

---

### Post by jaumety on 2012-04-03
no, però el que veig és que ho descomprimeix al directori on tinc els fitxers rpm. No ho se però crec que s'hauria de fer alguna altre cosa a mes d'executar alien.

---

### Post by wgarcia on 2012-04-04
En principi l'opció "-i" hauria d'instal·lar directament. Pots provar de no donar cap opció ("alien <paquet>.rpm") i veure si crea el fitxer deb, i després fer "dpkg -i <paquet>.deb" a veure si surt algun error d'instal·lació.

Si tot això falla l'altra via és descomprimir el fitxer "tar.gz", intentar compilar el paquet i intentar instal·lar-lo. Amb alguns paquets ben muntats és un procés més senzill del que sembla, però es necessita certa experiència per saber exactament què fer per completar el procés. A vegades hi ha algun fitxer "INSTALL" o alguna cosa així que explica el passos a donar.

---

