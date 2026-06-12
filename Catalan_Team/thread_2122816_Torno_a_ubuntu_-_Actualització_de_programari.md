---
title: "Torno a ubuntu - Actualització de programari"
date: 2013-03-06
forum: Catalan Team
---

### Post by ipelegri6 on 2013-03-06
Hola,

Després d'uns anys amb la linkat m'he decidit a tornar a ubuntu, sobretot per aquesta comunitat que tant em va ajudar quan tenia problemes :-)

Estic encantada amb el meu nou sistema operatiu (si haig de ser sincera, tant de bo hagués canviat abans...)

Avui, però, m'he trobat amb un avís en les actualitzacions:

------------------------------------------------------
No es pot inicialitzar la informació dels paquets

S'ha produït un error irresoluble mentre s'inicialitzava la informació de paquets.

Informeu d'aquest error de l'update-manager i incloeu el missatge següent:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en, E:No s'han pogut analitzar o obrir les llistes de paquets o el fitxer d'estat.'
-------------------------------------------------

Com que no sé qui és l'update-manager vinc aquí a veure si sabeu com ho puc resoldre. La versió que em van instal·lar (jo sola no me'n sortia) és la 12.04 . Alguna idea?

Irene

---

### Post by wgarcia on 2013-03-06
En primer lloc, benvinguda un altre cop, tot i que potser ha canviat una mica la gent des que vas estar per aquí fa un temps. 

En segon lloc, per arreglar el problema que tens, hauràs d'obrir una terminal (ALT-F2 i aquí entres: "terminal" i prems "intro") i en aquesta terminal entres:

```
sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial

```

Després entres

```
sudo apt-get update
sudo apt-get upgrade
```

això t'ho hauria d'arreglar.

---

### Post by ipelegri6 on 2013-03-06
Gràcies wgarcia!! De moment sembla que ha funcionat i ja torno a tenir el centre de programari en marxa :-)
De cap allà el 2008 recordo sobretot en papapep, hi vam passar unes quantes hores arreglant problemes que tenia, quina paciència que va tenir...

---

### Post by wgarcia on 2013-03-06
Sí, un mestre el papapep!

---

