---
title: "ttf-mscorefonts-installer"
date: 2016-09-20
forum: Catalan Team
---

### Post by jinglada on 2016-09-20
Bon dia,

Ahir, en el moment que es va solucionar el tema de la barra Unity i els menús ([https://ubuntuforums.org/showthread.php?t=2337313](https://ubuntuforums.org/showthread.php?t=2337313)) va sortit el següent missatge:

------------------------------------------------------------------------------------
Informació de l'actualització:

No s'han pogut baixar els fitxers de dades d'alguns paquets

Els paquets següents han sol·licitat baixar dades addicionals després de la
instal·lació del paquet, però no s'han pogut baixar o processar les dades.

ttf-mscorefonts-installer

Aquesta és una fallada permanent que deixa aquests paquets inservibles en
el vostre sistema. Heu d'arreglar la connexió a Internet, després suprimir
i tornar a instal·lar els paquets per solucionar aquest problema.
------------------------------------------------------------------------------------

Que cal fer?
Salutacions.

---

### Post by wgarcia on 2016-09-20
Prova si reinstal·lant el paquet ho arregla:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

---

### Post by jinglada on 2016-09-20
> **wgarcia said:**
> Prova si reinstal·lant el paquet ho arregla:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Gràcies wgarcia,

joan@joan-Aspire-E1-572:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer
[sudo] contrasenya per a joan: 
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
Els paquets següents s'han insta&#320;lat automàticament i ja no són necessaris:
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic
  linux-signed-image-4.4.0-34-generic
Empreu **«sudo apt autoremove»** per a suprimir-los.
0 actualitzats, 0 nous a insta&#320;lar, 1 reinsta&#320;lats, 0 a suprimir i 0 no actualitzats.
S'ha d'obtenir 29,5 kB d'arxius.
Després d'aquesta operació s'empraran 0 B d'espai en disc addicional.
Bai:1 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 ttf-mscorefonts-installer all 3.4+nmu1ubuntu2 [29,5 kB]
S'ha baixat 29,5 kB en 0s (79,5 kB/s)             
S'estan preconfigurant els paquets...
(S'està llegint la base de dades&#8230; hi ha 436496 fitxers i directoris instal·lats actualment.)
S'està preparant per a desempaquetar &#8230;/ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb&#8230;
mscorefonts-eula license has already been accepted
S'està desempaquetant ttf-mscorefonts-installer (3.4+nmu1ubuntu2) sobre (3.4+nmu1ubuntu2)&#8230;
S'estan processant els activadors per a fontconfig (2.11.94-0ubuntu1.1)&#8230;
S'estan processant els activadors per a update-notifier-common (3.168.1)&#8230;
S'està configurant ttf-mscorefonts-installer (3.4+nmu1ubuntu2)&#8230;
joan@joan-Aspire-E1-572:~$ **sudo apt autoremove**
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
Es SUPRIMIRAN els paquets següents:
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic linux-signed-image-4.4.0-34-generic
0 actualitzats, 0 nous a insta&#320;lar, 3 a suprimir i 0 no actualitzats.
Després d'aquesta operació s'alliberaran 218 MB d'espai en disc.
Voleu continuar? [S/n] 

He clicat "Intro".
...

És correcte, oi?

---

### Post by wgarcia on 2016-09-20
En principi sembla que sí. Per assegurar-te que el paquet ttf-mscorefonts-installer (l'instal·lador dels tipus de lletra de Microsoft, per exemple colibrí) pots donar ara: 

```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

Si et surt una pantalla on has d'acceptar la llicència d'aquests tipus de lletres, amb la tecla del tabulador pots navegar fins a OK i fer intro un cop ressaltis aquesta opció.

---

### Post by jinglada on 2016-09-21
> **wgarcia said:**
> En principi sembla que sí. Per assegurar-te que el paquet ttf-mscorefonts-installer (l'instal·lador dels tipus de lletra de Microsoft, per exemple colibrí) pots donar ara: 

```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

Si et surt una pantalla on has d'acceptar la llicència d'aquests tipus de lletres, amb la tecla del tabulador pots navegar fins a OK i fer intro un cop ressaltis aquesta opció.

Només ha sortit això:
joan@joan-Aspire-E1-572:~$ sudo dpkg-reconfigure ttf-mscorefonts-installer
[sudo] contrasenya per a joan: 
joan@joan-Aspire-E1-572:~$

---

### Post by wgarcia on 2016-09-21
Doncs sembla que ja està ben configurat. Si no veus res estrany, és que ha quedat tot bé.

---

